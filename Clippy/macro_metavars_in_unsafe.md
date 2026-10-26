Pattern: Macro metavariable expanded in `unsafe` block

Issue: -

## Description

This hides an unsafe block and allows the user of the macro to write unsafe code without an explicit
unsafe block at callsite, making it possible to perform unsafe operations in seemingly safe code.

The macro should be restructured so that these metavariables are referenced outside of unsafe blocks
and that the usual unsafety checks apply to the macro argument.

This is usually done by binding it to a variable outside of the unsafe block
and then using that variable inside of the block as shown in the example, or by referencing it a second time
in a safe context, e.g. `if false { $expr }`.

## What it does

Looks for macros that expand metavariables in an unsafe block.

## Examples

Example of **incorrect** code:

```rust
/// Gets the first element of a slice
macro_rules! first {
    ($slice:expr) => {
        unsafe {
            let slice = $slice; // ⚠️ expansion inside of `unsafe {}`

            assert!(!slice.is_empty());
            // SAFETY: slice is checked to have at least one element
            slice.first().unwrap_unchecked()
        }
    }
}

assert_eq!(*first!(&[1i32]), 1);

// This will compile as a consequence (note the lack of `unsafe {}`)
assert_eq!(*first!(std::hint::unreachable_unchecked() as &[i32]), 1);
```

Example of **correct** code:

```rust
macro_rules! first {
    ($slice:expr) => {{
        let slice = $slice; // ✅ outside of `unsafe {}`
        unsafe {
            assert!(!slice.is_empty());
            // SAFETY: slice is checked to have at least one element
            slice.first().unwrap_unchecked()
        }
    }}
}

assert_eq!(*first!(&[1]), 1);

// This won't compile:
assert_eq!(*first!(std::hint::unreachable_unchecked() as &[i32]), 1);
```

## Known limitations

Due to how macros are represented in the compiler at the time Clippy runs its lints,
it's not possible to look for metavariables in macro definitions directly.

Instead, this lint looks at expansions of macros.
This leads to false negatives for macros that are never actually invoked.

By default, this lint is rather conservative and will only emit warnings on publicly-exported
macros from the same crate, because oftentimes private internal macros are one-off macros where
this lint would just be noise (e.g. macros that generate `impl` blocks).
The default behavior should help with preventing a high number of such false positives,
however it can be configured to also emit warnings in private macros if desired.

## Further Reading

* [Clippy - macro_metavars_in_unsafe](https://clippy.rust-lang.org/stable/index.html#macro_metavars_in_unsafe)

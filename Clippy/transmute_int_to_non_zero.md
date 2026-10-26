Pattern: Transmute from integer to `NonZero`

Issue: -

## Description

Transmutes work on any types and thus might cause unsoundness when those types change
elsewhere. `new_unchecked` only works for the appropriate types instead.

## What it does

Checks for transmutes from `T` to `NonZero<T>`, and suggests the `new_unchecked`
method instead.

## Examples

Example of **incorrect** code:

```rust
let _: NonZero<u32> = unsafe { std::mem::transmute(123) };
```

Example of **correct** code:

```rust
let _: NonZero<u32> = unsafe { NonZero::new_unchecked(123) };
```

## Further Reading

* [Clippy - transmute_int_to_non_zero](https://clippy.rust-lang.org/stable/index.html#transmute_int_to_non_zero)

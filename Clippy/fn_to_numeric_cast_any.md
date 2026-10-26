Pattern: Function pointer cast to integer

Issue: -

## Description

Casting a function pointer to an integer can have surprising results and can occur
accidentally if parentheses are omitted from a function call. If you aren't doing anything
low-level with function pointers then you can opt out of casting functions to integers in
order to avoid mistakes. Alternatively, you can use this lint to audit all uses of function
pointer casts in your code.

## What it does

Checks for casts of a function pointer to any integer type.

## Examples

Example of **incorrect** code:

```rust
// fn1 is cast as `usize`
fn fn1() -> u16 {
    1
};
let _ = fn1 as usize;
```

Example of **correct** code:

```rust
// maybe you intended to call the function?
fn fn2() -> u16 {
    1
};
let _ = fn2() as usize;

// or

// maybe you intended to cast it to a function type?
fn fn3() -> u16 {
    1
}
let _ = fn3 as fn() -> u16;
```

## Further Reading

* [Clippy - fn_to_numeric_cast_any](https://clippy.rust-lang.org/stable/index.html#fn_to_numeric_cast_any)

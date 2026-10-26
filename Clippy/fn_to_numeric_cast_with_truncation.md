Pattern: Truncating function pointer cast

Issue: -

## Description

Such a cast discards some bits of the function's address. If this is intended, it would be more
clearly expressed by casting to `usize` first, then casting the `usize` to the intended type (with
a comment) to perform the truncation.

## What it does

Checks for casts of a function pointer to a numeric type not wide enough to
store an address.

## Examples

Example of **incorrect** code:

```rust
fn fn1() -> i16 {
    1
};
let _ = fn1 as i32;
```

Example of **correct** code:

```rust
// Cast to usize first, then comment with the reason for the truncation
fn fn1() -> i16 {
    1
};
let fn_ptr = fn1 as usize;
let fn_ptr_truncated = fn_ptr as i32;
```

## Further Reading

* [Clippy - fn_to_numeric_cast_with_truncation](https://clippy.rust-lang.org/stable/index.html#fn_to_numeric_cast_with_truncation)

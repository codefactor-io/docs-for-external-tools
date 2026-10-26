Pattern: Comparison with null pointer

Issue: -

## Description

It's easier and more readable to use the inherent
`.is_null()`
method instead

## What it does

This lint checks for equality comparisons with `ptr::null` or `ptr::null_mut`

## Examples

Example of **incorrect** code:

```rust
use std::ptr;

if x == ptr::null() {
    // ..
}
```

Example of **correct** code:

```rust
if x.is_null() {
    // ..
}
```

## Further Reading

* [Clippy - cmp_null](https://clippy.rust-lang.org/stable/index.html#cmp_null)

Pattern: Use of `as *const _` or `as *mut _`

Issue: -

## Description

The conversion might include a dangerous cast that might go undetected due to the type being inferred.

## What it does

Checks for the usage of `as *const _` or `as *mut _` conversion using inferred type.

## Examples

Example of **incorrect** code:

```rust
fn as_usize<T>(t: &T) -> usize {
    // BUG: `t` is already a reference, so we will here
    // return a dangling pointer to a temporary value instead
    &t as *const _ as usize
}
```

Example of **correct** code:

```rust
fn as_usize<T>(t: &T) -> usize {
    t as *const T as usize
}
```

## Further Reading

* [Clippy - as_pointer_underscore](https://clippy.rust-lang.org/stable/index.html#as_pointer_underscore)

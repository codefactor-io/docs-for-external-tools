Pattern: Redundant `pub(crate)` in private module

Issue: -

## Description

Writing `pub(crate)` is misleading when it's redundant due to the parent
module's visibility.

## What it does

Checks for items declared `pub(crate)` that are not crate visible because they
are inside a private module.

## Examples

```rust
mod internal {
    pub(crate) fn internal_fn() { }
}
```
This function is not visible outside the module and it can be declared with `pub` or
private visibility
```rust
mod internal {
    pub fn internal_fn() { }
}
```

## Further Reading

* [Clippy - redundant_pub_crate](https://clippy.rust-lang.org/stable/index.html#redundant_pub_crate)

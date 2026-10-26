Pattern: Implicit clone via `to_owned()` or similar

Issue: -

## Description

These methods do the same thing as `_.clone()` but may be confusing as
to why we are calling `to_vec` on something that is already a `Vec` or calling `to_owned` on something that is already owned.

## What it does

Checks for the usage of `_.to_owned()`, `vec.to_vec()`, or similar when calling `_.clone()` would be clearer.

## Examples

Example of **incorrect** code:

```rust
let a = vec![1, 2, 3];
let b = a.to_vec();
let c = a.to_owned();
```

Example of **correct** code:

```rust
let a = vec![1, 2, 3];
let b = a.clone();
let c = a.clone();
```

## Further Reading

* [Clippy - implicit_clone](https://clippy.rust-lang.org/stable/index.html#implicit_clone)

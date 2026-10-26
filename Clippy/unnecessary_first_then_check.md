Pattern: Use of `first()` to check emptiness

Issue: -

## Description

Using `.is_empty()` is shorter and better communicates the intention.

## What it does

Checks the usage of `.first().is_some()` or `.first().is_none()` to check if a slice is
empty.

## Examples

Example of **incorrect** code:

```rust
let v = vec![1, 2, 3];
if v.first().is_none() {
    // The vector is empty...
}
```

Example of **correct** code:

```rust
let v = vec![1, 2, 3];
if v.is_empty() {
    // The vector is empty...
}
```

## Further Reading

* [Clippy - unnecessary_first_then_check](https://clippy.rust-lang.org/stable/index.html#unnecessary_first_then_check)

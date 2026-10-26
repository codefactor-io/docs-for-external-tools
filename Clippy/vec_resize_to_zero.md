Pattern: Suspicious `Vec::resize(0, x)`

Issue: -

## Description

This is probably an argument inversion mistake.

## What it does

Finds occurrences of `Vec::resize(0, an_int)`

## Examples

Example of **incorrect** code:

```rust
vec![1, 2, 3, 4, 5].resize(0, 5)
```

Example of **correct** code:

```rust
vec![1, 2, 3, 4, 5].clear()
```

## Further Reading

* [Clippy - vec_resize_to_zero](https://clippy.rust-lang.org/stable/index.html#vec_resize_to_zero)

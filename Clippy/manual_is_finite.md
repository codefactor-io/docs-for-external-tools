Pattern: Missing use of `is_finite()`

Issue: -

## Description

The method `is_finite` is shorter and more readable.

## What it does

Checks for manual `is_finite` reimplementations
(i.e., `x != <float>::INFINITY && x != <float>::NEG_INFINITY`).

## Examples

Example of **incorrect** code:

```rust
if x != f32::INFINITY && x != f32::NEG_INFINITY {}
if x.abs() < f32::INFINITY {}
```

Example of **correct** code:

```rust
if x.is_finite() {}
if x.is_finite() {}
```

## Further Reading

* [Clippy - manual_is_finite](https://clippy.rust-lang.org/stable/index.html#manual_is_finite)

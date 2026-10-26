Pattern: Missing use of `is_infinite()`

Issue: -

## Description

The method `is_infinite` is shorter and more readable.

## What it does

Checks for manual `is_infinite` reimplementations
(i.e., `x == <float>::INFINITY || x == <float>::NEG_INFINITY`).

## Examples

Example of **incorrect** code:

```rust
if x == f32::INFINITY || x == f32::NEG_INFINITY {}
```

Example of **correct** code:

```rust
if x.is_infinite() {}
```

## Further Reading

* [Clippy - manual_is_infinite](https://clippy.rust-lang.org/stable/index.html#manual_is_infinite)

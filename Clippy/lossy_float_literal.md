Pattern: Lossy whole number float literal

Issue: -

## Description

If the value was intended to be exact, it will not be.
This may be especially surprising when the lost precision is to the left of the decimal point.

## What it does

Checks for whole number float literals that
cannot be represented as the underlying type without loss.

## Examples

Example of **incorrect** code:

```rust
let _: f32 = 16_777_217.0; // 16_777_216.0
```

Example of **correct** code:

```rust
let _: f32 = 16_777_216.0;
let _: f64 = 16_777_217.0;
```

## Further Reading

* [Clippy - lossy_float_literal](https://clippy.rust-lang.org/stable/index.html#lossy_float_literal)

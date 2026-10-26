Pattern: Use of `0.0 / 0.0` for NaN

Issue: -

## Description

It's less readable than `f32::NAN` or `f64::NAN`.

## What it does

Checks for `0.0 / 0.0`.

## Examples

Example of **incorrect** code:

```rust
let nan = 0.0f32 / 0.0;
```

Example of **correct** code:

```rust
let nan = f32::NAN;
```

## Further Reading

* [Clippy - zero_divided_by_zero](https://clippy.rust-lang.org/stable/index.html#zero_divided_by_zero)

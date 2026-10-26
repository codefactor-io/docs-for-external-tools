Pattern: Use of legacy numeric constant

Issue: -

## Description

All of these have been superseded by the associated constants on their respective types,
such as `i128::MAX`. These legacy items may be deprecated in a future version of rust.

## What it does

Checks for usage of `<integer>::max_value()`, `std::<integer>::MAX`,
`std::<float>::EPSILON`, etc.

## Examples

Example of **incorrect** code:

```rust
let eps = std::f32::EPSILON;
```

Example of **correct** code:

```rust
let eps = f32::EPSILON;
```

## Further Reading

* [Clippy - legacy_numeric_constants](https://clippy.rust-lang.org/stable/index.html#legacy_numeric_constants)

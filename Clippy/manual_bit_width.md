Pattern: Missing use of `bit_width()`

Issue: -

## Description

Manual reimplementations of `bit_width` increase code complexity for little benefit.

## What it does

Checks for usage of `T::BITS - x.leading_zeros()` when `x.bit_width()` is available.

## Examples

Example of **incorrect** code:

```rust
let x: u32 = 5;
let bit_width = u32::BITS - x.leading_zeros();
```

Example of **correct** code:

```rust
let x: u32 = 5;
let bit_width = x.bit_width();
```

## Further Reading

* [Clippy - manual_bit_width](https://clippy.rust-lang.org/stable/index.html#manual_bit_width)

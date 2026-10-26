Pattern: Mismatched types in bit width calculation

Issue: -

## Description

Substracting `leading_zeros` from the number of bits of another type might be
a buggy implementation of the `bit_width` method.

## What it does

Checks for usage of `T::BITS - x.leading_zeros()` where T and x are of different types.

## Examples

Example of **incorrect** code:

```rust
let x: u64 = 5;
let bit_width = u32::BITS - x.leading_zeros();
```

Example of **correct** code:

```rust
let x: u64 = 5;
let bit_width = x.bit_width();
```

## Further Reading

* [Clippy - mismatched_bit_width_type](https://clippy.rust-lang.org/stable/index.html#mismatched_bit_width_type)

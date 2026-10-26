Pattern: Cast to float with precision loss

Issue: -

## Description

It's not bad at all. But in some applications it can be
helpful to know where precision loss can take place. This lint can help find
those places in the code.

## What it does

Checks for casts from any numeric type to a float type where
the receiving type cannot store all values from the original type without
rounding errors. This possible rounding is to be expected, so this lint is
`Allow` by default.

Basically, this warns on casting any integer with 32 or more bits to `f32`
or any 64-bit integer to `f64`.

## Examples

Example of **incorrect** code:

```rust
let x = u64::MAX;
x as f64;
```

## Further Reading

* [Clippy - cast_precision_loss](https://clippy.rust-lang.org/stable/index.html#cast_precision_loss)

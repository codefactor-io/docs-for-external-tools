Pattern: Cast of `NaN` to integer

Issue: -

## Description

NaNs are cast into zero, so one could simply use this and make the
code more readable. The lint could also hint at a programmer error.

## What it does

Checks for a known NaN float being cast to an integer

## Examples

Example of **incorrect** code:

```rust
let _ = (0.0_f32 / 0.0) as u64;
```

Example of **correct** code:

```rust
let _ = 0_u64;
```

## Further Reading

* [Clippy - cast_nan_to_int](https://clippy.rust-lang.org/stable/index.html#cast_nan_to_int)

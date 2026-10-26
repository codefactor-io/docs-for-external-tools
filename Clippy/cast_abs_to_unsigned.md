Pattern: Cast of `abs()` result to unsigned type

Issue: -

## Description

The `unsigned_abs()` method avoids panic when called on the MIN value.

## What it does

Checks for usage of the `abs()` method that cast the result to unsigned.

## Examples

Example of **incorrect** code:

```rust
let x: i32 = -42;
let y: u32 = x.abs() as u32;
```

Example of **correct** code:

```rust
let x: i32 = -42;
let y: u32 = x.unsigned_abs();
```

## Further Reading

* [Clippy - cast_abs_to_unsigned](https://clippy.rust-lang.org/stable/index.html#cast_abs_to_unsigned)

Pattern: Midpoint calculation that can overflow

Issue: -

## Description

Using `(x + y) / 2` or `(x + y) >> 1` on integer types might cause an overflow on the
intermediate addition result. The latter will only warn for unsigned integer types.
Similar for floating-point `(x + y) / 2.0` and `(x + y) * 0.5`.

## What it does

Checks for manual implementation of `midpoint`.

## Examples

Example of **incorrect** code:

```rust
let c = (a + 10) / 2;
let d = (a + 10) >> 1;
let b: f32 = 0.0;
let e = (b + 10.0) / 2.0;
let f = (b + 10.0) * 0.5;
```

Example of **correct** code:

```rust
let c = u32::midpoint(a, 10);
let d = u32::midpoint(a, 10);
let b: f32 = 0.0;
let e = f32::midpoint(b, 10.0);
let f = f32::midpoint(b, 10.0);
```

## Further Reading

* [Clippy - manual_midpoint](https://clippy.rust-lang.org/stable/index.html#manual_midpoint)

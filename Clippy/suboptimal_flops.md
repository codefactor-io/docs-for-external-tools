Pattern: Suboptimal floating-point operation

Issue: -

## Description

Negatively impacts accuracy and performance.

## What it does

Looks for floating-point expressions that
can be expressed using built-in methods to improve both
accuracy and performance.

## Examples

```rust
use std::f32::consts::E;

let a = 3f32;
let _ = (2f32).powf(a);
let _ = E.powf(a);
let _ = a.powf(1.0 / 2.0);
let _ = a.log(2.0);
let _ = a.log(10.0);
let _ = a.log(E);
let _ = a.powf(2.0);
let _ = a * 2.0 + 4.0;
let _ = if a < 0.0 {
    -a
} else {
    a
};
let _ = if a < 0.0 {
    a
} else {
    -a
};
```

is better expressed as

```rust
use std::f32::consts::E;

let a = 3f32;
let _ = a.exp2();
let _ = a.exp();
let _ = a.sqrt();
let _ = a.log2();
let _ = a.log10();
let _ = a.ln();
let _ = a.powi(2);
let _ = a.mul_add(2.0, 4.0);
let _ = a.abs();
let _ = -a.abs();
```

## Further Reading

* [Clippy - suboptimal_flops](https://clippy.rust-lang.org/stable/index.html#suboptimal_flops)

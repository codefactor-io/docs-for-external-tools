Pattern: Imprecise floating-point operation

Issue: -

## Description

Negatively impacts accuracy.

## What it does

Looks for floating-point expressions that
can be expressed using built-in methods to improve accuracy
at the cost of performance.

## Examples

Example of **incorrect** code:

```rust
let a = 3f32;
let _ = a.powf(1.0 / 3.0);
let _ = (1.0 + a).ln();
let _ = a.exp() - 1.0;
```

Example of **correct** code:

```rust
let a = 3f32;
let _ = a.cbrt();
let _ = a.ln_1p();
let _ = a.exp_m1();
```

## Further Reading

* [Clippy - imprecise_flops](https://clippy.rust-lang.org/stable/index.html#imprecise_flops)

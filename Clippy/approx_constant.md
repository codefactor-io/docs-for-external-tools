Pattern: Approximation of known float constant

Issue: -

## Description

Usually, the definition in the standard library is more
precise than what people come up with. If you find that your definition is
actually more precise, please [file a Rust
issue](https://github.com/rust-lang/rust/issues).

## What it does

Checks for floating point literals that approximate
constants which are defined in
[`std::f32::consts`](https://doc.rust-lang.org/stable/std/f32/consts/#constants)
or
[`std::f64::consts`](https://doc.rust-lang.org/stable/std/f64/consts/#constants),
respectively, suggesting to use the predefined constant.

## Examples

Example of **incorrect** code:

```rust
let x = 3.14;
let y = 1_f64 / x;
```

Example of **correct** code:

```rust
let x = std::f32::consts::PI;
let y = std::f64::consts::FRAC_1_PI;
```

## Further Reading

* [Clippy - approx_constant](https://clippy.rust-lang.org/stable/index.html#approx_constant)

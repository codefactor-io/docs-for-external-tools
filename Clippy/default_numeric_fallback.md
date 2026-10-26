Pattern: Unconstrained numeric literal

Issue: -

## Description

To ensure that every numeric type is chosen explicitly rather than implicitly.

## What it does

Checks for usage of unconstrained numeric literals which may cause default numeric fallback in type
inference.

Default numeric fallback means that if numeric types have not yet been bound to concrete
types at the end of type inference, then integer type is bound to `i32`, and similarly
floating type is bound to `f64`.

See [RFC0212](https://github.com/rust-lang/rfcs/blob/master/text/0212-restore-int-fallback.md) for more information about the fallback.

## Examples

Example of **incorrect** code:

```rust
let i = 10;
let f = 1.23;
```

Example of **correct** code:

```rust
let i = 10_i32;
let f = 1.23_f64;
```

## Known problems

This lint is implemented using a custom algorithm independent of rustc's inference,
which results in many false positives and false negatives.

## Further Reading

* [Clippy - default_numeric_fallback](https://clippy.rust-lang.org/stable/index.html#default_numeric_fallback)

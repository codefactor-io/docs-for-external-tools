Pattern: Missing use of `ilog2()`

Issue: -

## Description

Manual reimplementations of `ilog2` increase code complexity for little benefit.

## What it does

Checks for expressions like `N - x.leading_zeros()` (where `N` is one less than bit width
of `x`) or `x.ilog(2)`, which are manual reimplementations of `x.ilog2()`

## Examples

Example of **incorrect** code:

```rust
let x: u32 = 5;
let log = 31 - x.leading_zeros();
let log = x.ilog(2);
```

Example of **correct** code:

```rust
let x: u32 = 5;
let log = x.ilog2();
let log = x.ilog2();
```

## Further Reading

* [Clippy - manual_ilog2](https://clippy.rust-lang.org/stable/index.html#manual_ilog2)

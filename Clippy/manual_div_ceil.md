Pattern: Missing use of `div_ceil()`

Issue: -

## Description

It's simpler, clearer and more readable.

## What it does

Checks for an expression like `(x + (y - 1)) / y` which is a common manual reimplementation
of `x.div_ceil(y)`.

## Examples

Example of **incorrect** code:

```rust
let x: i32 = 7;
let y: i32 = 4;
let div = (x + (y - 1)) / y;
```

Example of **correct** code:

```rust
#![feature(int_roundings)]
let x: i32 = 7;
let y: i32 = 4;
let div = x.div_ceil(y);
```

## Further Reading

* [Clippy - manual_div_ceil](https://clippy.rust-lang.org/stable/index.html#manual_div_ceil)

Pattern: Missing use of `isolate_lowest_one()`

Issue: -

## Description

The manual bit-twiddling forms are harder to read than the standard library method.
Using `-x` can also overflow for signed minimum values.

## What it does

Checks for manual implementations of isolating the lowest set bit.

## Examples

Example of **incorrect** code:

```rust
let x: u32 = 5;
let lsb = x & x.wrapping_neg();
```

Example of **correct** code:

```rust
let x: u32 = 5;
let lsb = x.isolate_lowest_one();
```

## Further Reading

* [Clippy - manual_isolate_lowest_one](https://clippy.rust-lang.org/stable/index.html#manual_isolate_lowest_one)

Pattern: Large digit groups in literal

Issue: -

## Description

Negatively impacts readability.

## What it does

Warns if the digits of an integral or floating-point
constant are grouped into groups that
are too large.

## Examples

Example of **incorrect** code:

```rust
let x: u64 = 6186491_8973511;
```

## Further Reading

* [Clippy - large_digit_groups](https://clippy.rust-lang.org/stable/index.html#large_digit_groups)

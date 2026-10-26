Pattern: Redundant double comparison

Issue: -

## Description

Only one of the comparisons has any effect on the result, the programmer
probably intended to flip one of the comparison operators, or compare a
different value entirely.

## What it does

Checks for ineffective double comparisons against constants.

## Examples

Example of **incorrect** code:

```rust
if status_code <= 400 && status_code < 500 {}
```

## Further Reading

* [Clippy - redundant_comparisons](https://clippy.rust-lang.org/stable/index.html#redundant_comparisons)

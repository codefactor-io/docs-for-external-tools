Pattern: Double comparison of same operands

Issue: -

## Description

Readability.

## What it does

Checks for double comparisons that could be simplified to a single expression.

## Examples

Example of **incorrect** code:

```rust
if x == y || x < y {}
```

Example of **correct** code:

```rust
if x <= y {}
```

## Further Reading

* [Clippy - double_comparisons](https://clippy.rust-lang.org/stable/index.html#double_comparisons)

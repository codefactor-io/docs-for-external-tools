Pattern: Use of floating-point arithmetic

Issue: -

## Description

For some embedded systems or kernel development, it
can be useful to rule out floating-point numbers.

## What it does

Checks for float arithmetic.

## Examples

Example of **incorrect** code:

```rust
a + 1.0;
```

## Further Reading

* [Clippy - float_arithmetic](https://clippy.rust-lang.org/stable/index.html#float_arithmetic)

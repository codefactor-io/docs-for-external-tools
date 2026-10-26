Pattern: Unclear precedence of bit shift and mask

Issue: -

## Description

Not everyone knows the precedence of those operators by
heart, so expressions like these may trip others trying to reason about the
code.

## What it does

Checks for bit shifting operations combined with bit masking/combining operators
and suggest using parentheses.

## Examples

`0x2345 & 0xF000 >> 12` equals 5, while `(0x2345 & 0xF000) >> 12` equals 2

## Further Reading

* [Clippy - precedence_bits](https://clippy.rust-lang.org/stable/index.html#precedence_bits)

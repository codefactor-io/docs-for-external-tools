Pattern: Unclear operator precedence

Issue: -

## Description

Not everyone knows the precedence of those operators by
heart, so expressions like these may trip others trying to reason about the
code.

## What it does

Checks for operations where precedence may be unclear and suggests to add parentheses.
It catches a mixed usage of arithmetic and bit shifting/combining operators,
as well as method calls applied to closures.

## Examples

`1 << 2 + 3` equals 32, while `(1 << 2) + 3` equals 7

## Further Reading

* [Clippy - precedence](https://clippy.rust-lang.org/stable/index.html#precedence)

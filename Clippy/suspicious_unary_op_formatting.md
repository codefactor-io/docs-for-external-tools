Pattern: Suspicious unary operator formatting

Issue: -

## Description

This is either a typo in the binary operator or confusing.

## What it does

Checks the formatting of a unary operator on the right hand side
of a binary operator. It lints if there is no space between the binary and unary operators,
but there is a space between the unary and its operand.

## Examples

Example of **incorrect** code:

```rust
// &&! looks like a different operator
if foo &&! bar {}
```

Example of **correct** code:

```rust
if foo && !bar {}
```

## Further Reading

* [Clippy - suspicious_unary_op_formatting](https://clippy.rust-lang.org/stable/index.html#suspicious_unary_op_formatting)

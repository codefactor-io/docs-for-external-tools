Pattern: Suspicious `=*`, `=!` or `=-` formatting

Issue: -

## Description

This is either a typo of `*=`, `!=` or `-=` or
confusing.

## What it does

Checks for usage of the non-existent `=*`, `=!` and `=-`
operators.

## Examples

Example of **incorrect** code:

```rust
a =- 42; // confusing, should it be `a -= 42` or `a = -42`?
```

## Further Reading

* [Clippy - suspicious_assignment_formatting](https://clippy.rust-lang.org/stable/index.html#suspicious_assignment_formatting)

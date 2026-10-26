Pattern: Outer expression with no effect

Issue: -

## Description

Expressions by themselves often have no side-effects.
Having such expressions reduces readability.

## What it does

Checks for expression statements that can be reduced to a
sub-expression.

## Examples

Example of **incorrect** code:

```rust
compute_array()[0];
```

## Further Reading

* [Clippy - unnecessary_operation](https://clippy.rust-lang.org/stable/index.html#unnecessary_operation)

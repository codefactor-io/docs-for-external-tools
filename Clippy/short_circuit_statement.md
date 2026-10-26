Pattern: Short-circuit condition used as statement

Issue: -

## Description

Using a short circuit boolean condition as a statement
may hide the fact that the second part is executed or not depending on the
outcome of the first part.

## What it does

Checks for the use of short circuit boolean conditions as
a
statement.

## Examples

Example of **incorrect** code:

```rust
f() && g(); // We should write `if f() { g(); }`.
```

## Further Reading

* [Clippy - short_circuit_statement](https://clippy.rust-lang.org/stable/index.html#short_circuit_statement)

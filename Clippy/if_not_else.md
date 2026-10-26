Pattern: Negated condition in `if` with `else`

Issue: -

## Description

Negations reduce the readability of statements.

## What it does

Checks for usage of `!` or `!=` in an if condition with an
else branch.

## Examples

Example of **incorrect** code:

```rust
if !v.is_empty() {
    a()
} else {
    b()
}
```

Example of **correct** code:

```rust
if v.is_empty() {
    b()
} else {
    a()
}
```

## Further Reading

* [Clippy - if_not_else](https://clippy.rust-lang.org/stable/index.html#if_not_else)

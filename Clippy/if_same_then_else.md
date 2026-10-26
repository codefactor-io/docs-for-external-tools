Pattern: Identical `if` and `else` blocks

Issue: -

## Description

This is probably a copy & paste error.

## What it does

Checks for `if/else` with the same body as the *then* part
and the *else* part.

## Examples

Example of **incorrect** code:

```rust
let foo = if … {
    42
} else {
    42
};
```

## Further Reading

* [Clippy - if_same_then_else](https://clippy.rust-lang.org/stable/index.html#if_same_then_else)

Pattern: Identity operation like `x + 0`

Issue: -

## Description

This code can be removed without changing the
meaning. So it just obscures what's going on. Delete it mercilessly.

## What it does

Checks for identity operations, e.g., `x + 0`.

## Examples

Example of **incorrect** code:

```rust
x / 1 + 0 * 1 - 0 | 0;
```

## Further Reading

* [Clippy - identity_op](https://clippy.rust-lang.org/stable/index.html#identity_op)

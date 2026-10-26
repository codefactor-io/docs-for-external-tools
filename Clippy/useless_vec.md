Pattern: Useless `vec!`

Issue: -

## Description

This is less efficient.

## What it does

Checks for usage of `vec![..]` when using `[..]` would
be possible.

## Examples

Example of **incorrect** code:

```rust
fn foo(_x: &[u8]) {}

foo(&vec![1, 2]);
```

Example of **correct** code:

```rust
foo(&[1, 2]);
```

## Further Reading

* [Clippy - useless_vec](https://clippy.rust-lang.org/stable/index.html#useless_vec)

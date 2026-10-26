Pattern: Missing use of `let...else`

Issue: -

## Description

`let...else` provides a standard construct for this pattern
that people can easily recognize. It's also more compact.

## What it does

Warn of cases where `let...else` could be used

## Examples

Example of **incorrect** code:

```rust
let v = if let Some(v) = w { v } else { return };
```

Example of **correct** code:

```rust
let Some(v) = w else { return };
```

## Further Reading

* [Clippy - manual_let_else](https://clippy.rust-lang.org/stable/index.html#manual_let_else)

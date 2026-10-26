Pattern: Rounding of whole-number float literal

Issue: -

## Description

This is unnecessary and confusing to the reader. Doing this is probably a mistake.

## What it does

Detects cases where a whole-number literal float is being rounded, using
the `floor`, `ceil`, or `round` methods.

## Examples

Example of **incorrect** code:

```rust
let x = 1f32.ceil();
```

Example of **correct** code:

```rust
let x = 1f32;
```

## Further Reading

* [Clippy - unused_rounding](https://clippy.rust-lang.org/stable/index.html#unused_rounding)

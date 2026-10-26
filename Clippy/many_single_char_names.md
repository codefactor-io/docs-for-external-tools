Pattern: Too many single-character bindings

Issue: -

## Description

It's hard to memorize what a variable means without a
descriptive name.

## What it does

Checks for too many variables whose name consists of a
single character.

## Examples

Example of **incorrect** code:

```rust
let (a, b, c, d, e, f, g) = (...);
```

## Further Reading

* [Clippy - many_single_char_names](https://clippy.rust-lang.org/stable/index.html#many_single_char_names)

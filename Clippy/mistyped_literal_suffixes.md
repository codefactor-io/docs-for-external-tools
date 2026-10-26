Pattern: Mistyped literal suffix

Issue: -

## Description

This is most probably a typo

## What it does

Warns for mistyped suffix in literals

## Examples

Example of **incorrect** code:

```rust
`2_32` => `2_i32`
`250_8 => `250_u8`
```

## Known problems

- Does not match on integers too large to fit in the corresponding unsigned type
- Does not match on `_127` since that is a valid grouping for decimal and octal numbers

## Further Reading

* [Clippy - mistyped_literal_suffixes](https://clippy.rust-lang.org/stable/index.html#mistyped_literal_suffixes)

Pattern: Possible missing comma in array

Issue: -

## Description

This could lead to unexpected results.

## What it does

Checks for possible missing comma in an array. It lints if
an array element is a binary operator expression and it lies on two lines.

## Examples

Example of **incorrect** code:

```rust
let a = &[
    -1, -2, -3 // <= no comma here
    -4, -5, -6
];
```

## Further Reading

* [Clippy - possible_missing_comma](https://clippy.rust-lang.org/stable/index.html#possible_missing_comma)

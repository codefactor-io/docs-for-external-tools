Pattern: Missing use of `Iterator::enumerate()`

Issue: -

## Description

The code is better expressed with `.enumerate()`.

## What it does

Checks for zipping a collection with the range of
`0.._.len()`.

## Examples

Example of **incorrect** code:

```rust
let _ = x.iter().zip(0..x.len());
```

Example of **correct** code:

```rust
let _ = x.iter().enumerate();
```

## Further Reading

* [Clippy - range_zip_with_len](https://clippy.rust-lang.org/stable/index.html#range_zip_with_len)

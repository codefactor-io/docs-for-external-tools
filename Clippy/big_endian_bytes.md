Pattern: Use of `to_be_bytes()` or `from_be_bytes()`

Issue: -

## Description

To ensure use of little-endian or the target’s endianness rather than big-endian.

## What it does

Checks for the usage of the `to_be_bytes` method and/or the function `from_be_bytes`.

## Examples

Example of **incorrect** code:

```rust
let _x = 2i32.to_be_bytes();
let _y = 2i64.to_be_bytes();
```

## Further Reading

* [Clippy - big_endian_bytes](https://clippy.rust-lang.org/stable/index.html#big_endian_bytes)

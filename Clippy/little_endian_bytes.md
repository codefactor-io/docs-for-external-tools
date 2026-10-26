Pattern: Use of little-endian byte conversion

Issue: -

## Description

To ensure use of big-endian or the target’s endianness rather than little-endian.

## What it does

Checks for the usage of the `to_le_bytes` method and/or the function `from_le_bytes`.

## Examples

Example of **incorrect** code:

```rust
let _x = 2i32.to_le_bytes();
let _y = 2i64.to_le_bytes();
```

## Further Reading

* [Clippy - little_endian_bytes](https://clippy.rust-lang.org/stable/index.html#little_endian_bytes)

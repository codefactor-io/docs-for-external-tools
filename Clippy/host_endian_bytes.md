Pattern: Use of `to_ne_bytes()` or `from_ne_bytes()`

Issue: -

## Description

To ensure use of explicitly chosen endianness rather than the target’s endianness,
such as when implementing network protocols or file formats rather than FFI.

## What it does

Checks for the usage of the `to_ne_bytes` method and/or the function `from_ne_bytes`.

## Examples

Example of **incorrect** code:

```rust
let _x = 2i32.to_ne_bytes();
let _y = 2i64.to_ne_bytes();
```

## Further Reading

* [Clippy - host_endian_bytes](https://clippy.rust-lang.org/stable/index.html#host_endian_bytes)

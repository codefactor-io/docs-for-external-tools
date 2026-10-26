Pattern: Unusual digit grouping in hex or binary literal

Issue: -

## Description

Negatively impacts readability.

## What it does

Warns if hexadecimal or binary literals are not grouped
by nibble or byte.

## Examples

Example of **incorrect** code:

```rust
let x: u32 = 0xFFF_FFF;
let y: u8 = 0b01_011_101;
```

## Further Reading

* [Clippy - unusual_byte_groupings](https://clippy.rust-lang.org/stable/index.html#unusual_byte_groupings)

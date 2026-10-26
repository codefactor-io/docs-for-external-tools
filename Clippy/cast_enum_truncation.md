Pattern: Truncating cast from enum to integer

Issue: -

## Description

The resulting integral value will not match the value of the variant it came from.

## What it does

Checks for casts from an enum type to an integral type that will definitely truncate the
value.

## Examples

Example of **incorrect** code:

```rust
enum E { X = 256 };
let _ = E::X as u8;
```

## Further Reading

* [Clippy - cast_enum_truncation](https://clippy.rust-lang.org/stable/index.html#cast_enum_truncation)

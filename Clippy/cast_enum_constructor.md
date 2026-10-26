Pattern: Cast of enum tuple constructor to integer

Issue: -

## Description

The cast is easily confused with casting a c-like enum value to an integer.

## What it does

Checks for casts from an enum tuple constructor to an integer.

## Examples

Example of **incorrect** code:

```rust
enum E { X(i32) };
let _ = E::X as usize;
```

## Further Reading

* [Clippy - cast_enum_constructor](https://clippy.rust-lang.org/stable/index.html#cast_enum_constructor)

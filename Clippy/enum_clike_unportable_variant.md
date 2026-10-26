Pattern: C-like enum value not fitting in `i32`

Issue: -

## Description

This will truncate the variant value on 32 bit
architectures, but works fine on 64 bit.

## What it does

Checks for C-like enumerations that are
`repr(isize/usize)` and have values that don't fit into an `i32`.

## Examples

Example of **incorrect** code:

```rust
#[repr(usize)]
enum NonPortable {
    X = 0x1_0000_0000,
    Y = 0,
}
```

## Further Reading

* [Clippy - enum_clike_unportable_variant](https://clippy.rust-lang.org/stable/index.html#enum_clike_unportable_variant)

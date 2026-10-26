Pattern: Struct with partially public fields

Issue: -

## Description

Most types should either be:
* Abstract data types: complex objects with opaque implementation which guard
  interior invariants and expose intentionally limited API to the outside world.
* Data: relatively simple objects which group a bunch of related attributes together,
  but have no invariants.

## What it does

Checks whether some but not all fields of a `struct` are public.

Either make all fields of a type public, or make none of them public

## Examples

Example of **incorrect** code:

```rust
pub struct Color {
    pub r: u8,
    pub g: u8,
    b: u8,
}
```

Example of **correct** code:

```rust
pub struct Color {
    pub r: u8,
    pub g: u8,
    pub b: u8,
}
```

## Further Reading

* [Clippy - partial_pub_fields](https://clippy.rust-lang.org/stable/index.html#partial_pub_fields)

Pattern: Mixed inner and outer attributes

Issue: -

## Description

Having both style of said attributes makes it more complicated to read code.

## What it does

Checks for items that have the same kind of attributes with mixed styles (inner/outer).

## Examples

Example of **incorrect** code:

```rust
#[cfg(linux)]
pub fn foo() {
    #![cfg(windows)]
}
```

Example of **correct** code:

```rust
#[cfg(linux)]
#[cfg(windows)]
pub fn foo() {
}
```

## Known problems

This lint currently has false-negatives when mixing same attributes
but they have different path symbols, for example:
```rust
#[custom_attribute]
pub fn foo() {
    #![my_crate::custom_attribute]
}
```

## Further Reading

* [Clippy - mixed_attributes_style](https://clippy.rust-lang.org/stable/index.html#mixed_attributes_style)

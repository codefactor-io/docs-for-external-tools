Pattern: `let` binding of unit value

Issue: -

## Description

A unit value cannot usefully be used anywhere. So
binding one is kind of pointless.

## What it does

Checks for binding a unit value.

## Examples

Example of **incorrect** code:

```rust
let x = {
    1;
};
```

## Further Reading

* [Clippy - let_unit_value](https://clippy.rust-lang.org/stable/index.html#let_unit_value)

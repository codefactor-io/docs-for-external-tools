Pattern: Decimal literal instead of hexadecimal

Issue: -

## Description

Especially for big powers of 2, a hexadecimal representation is usually more
readable than a decimal representation.

## What it does

Warns if there is a better representation for a numeric literal.

## Examples

Example of **incorrect** code:

```text
`255` => `0xFF`
`65_535` => `0xFFFF`
`4_042_322_160` => `0xF0F0_F0F0`
```

## Further Reading

* [Clippy - decimal_literal_representation](https://clippy.rust-lang.org/stable/index.html#decimal_literal_representation)

Pattern: Decimal literal in bitwise operation

Issue: -

## Description

Using decimal literals for bit masks can make the code less readable and obscure the intended bit pattern.
Binary, hexadecimal, or octal literals make the bit pattern more explicit and easier to understand at a glance.

## What it does

Checks for decimal literals used as bit masks in bitwise operations.

## Examples

Example of **incorrect** code:

```rust
let a = 14 & 6; // Bit pattern is not immediately clear
```

Example of **correct** code:

```rust
let a = 0b1110 & 0b0110;
```

## Further Reading

* [Clippy - decimal_bitwise_operands](https://clippy.rust-lang.org/stable/index.html#decimal_bitwise_operands)

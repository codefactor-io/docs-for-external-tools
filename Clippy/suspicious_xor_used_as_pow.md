Pattern: Possible XOR `^` used as exponentiation

Issue: -

## Description

It's most probably a typo and may lead to unexpected behaviours.

## What it does

Warns for a Bitwise XOR (`^`) operator being probably confused as a powering. It will not trigger if any of the numbers are not in decimal.

## Examples

Example of **incorrect** code:

```rust
let x = 3_i32 ^ 4_i32;
```

Example of **correct** code:

```rust
let x = 3_i32.pow(4);
```

## Further Reading

* [Clippy - suspicious_xor_used_as_pow](https://clippy.rust-lang.org/stable/index.html#suspicious_xor_used_as_pow)

Pattern: Mixed-case hex literal

Issue: -

## Description

It looks confusing.

## What it does

Warns on hexadecimal literals with mixed-case letter
digits.

## Examples

Example of **incorrect** code:

```rust
0x1a9BAcD
```

Example of **correct** code:

```rust
0x1A9BACD
```

## Further Reading

* [Clippy - mixed_case_hex_literals](https://clippy.rust-lang.org/stable/index.html#mixed_case_hex_literals)

Pattern: Long literal without underscores

Issue: -

## Description

Reading long numbers is difficult without separators.

## What it does

Warns if a long integral or floating-point constant does
not contain underscores.

## Examples

Example of **incorrect** code:

```rust
61864918973511
```

Example of **correct** code:

```rust
61_864_918_973_511
```

## Further Reading

* [Clippy - unreadable_literal](https://clippy.rust-lang.org/stable/index.html#unreadable_literal)

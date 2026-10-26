Pattern: Inconsistent digit grouping in literal

Issue: -

## Description

Readers may incorrectly interpret inconsistently
grouped digits.

## What it does

Warns if an integral or floating-point constant is
grouped inconsistently with underscores.

## Examples

Example of **incorrect** code:

```rust
618_64_9189_73_511
```

Example of **correct** code:

```rust
61_864_918_973_511
```

## Further Reading

* [Clippy - inconsistent_digit_grouping](https://clippy.rust-lang.org/stable/index.html#inconsistent_digit_grouping)

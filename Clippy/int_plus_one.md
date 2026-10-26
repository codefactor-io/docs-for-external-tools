Pattern: Use of `x >= y + 1` comparison

Issue: -

## Description

Readability -- better to use `> y` instead of `>= y + 1`.

## What it does

Checks for usage of `x >= y + 1` or `x - 1 >= y` (and `<=`) in a block

## Examples

Example of **incorrect** code:

```rust
if x >= y + 1 {}
```

Example of **correct** code:

```rust
if x > y {}
```

## Further Reading

* [Clippy - int_plus_one](https://clippy.rust-lang.org/stable/index.html#int_plus_one)

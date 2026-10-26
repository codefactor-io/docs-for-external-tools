Pattern: Missing use of saturating arithmetic

Issue: -

## Description

These can be written simply with `saturating_add/sub` methods.

## What it does

Checks for `.checked_add/sub(x).unwrap_or(MAX/MIN)`.

## Examples

```rust
let add = x.checked_add(y).unwrap_or(u32::MAX);
let sub = x.checked_sub(y).unwrap_or(u32::MIN);
```

can be written using dedicated methods for saturating addition/subtraction as:

```rust
let add = x.saturating_add(y);
let sub = x.saturating_sub(y);
```

## Further Reading

* [Clippy - manual_saturating_arithmetic](https://clippy.rust-lang.org/stable/index.html#manual_saturating_arithmetic)

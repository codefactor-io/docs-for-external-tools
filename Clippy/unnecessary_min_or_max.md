Pattern: Unnecessary `min()` or `max()` call

Issue: -

## Description

In the aforementioned cases it is not necessary to call `min()` or `max()`
to compare values, it may even cause confusion.

## What it does

Checks for unnecessary calls to `min()` or `max()` in the following cases
- Either both side is constant
- One side is clearly larger than the other, like i32::MIN and an i32 variable

## Examples

Example of **incorrect** code:

```rust
let _ = 0.min(7_u32);
```

Example of **correct** code:

```rust
let _ = 0;
```

## Further Reading

* [Clippy - unnecessary_min_or_max](https://clippy.rust-lang.org/stable/index.html#unnecessary_min_or_max)

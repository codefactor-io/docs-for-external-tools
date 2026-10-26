Pattern: Missing use of `try_from()`

Issue: -

## Description

Reduces the readability of statements & is error prone.

## What it does

Checks for explicit bounds checking when casting.

## Examples

Example of **incorrect** code:

```rust
foo <= i32::MAX as u32;
```

Example of **correct** code:

```rust
i32::try_from(foo).is_ok();
```

## Further Reading

* [Clippy - checked_conversions](https://clippy.rust-lang.org/stable/index.html#checked_conversions)

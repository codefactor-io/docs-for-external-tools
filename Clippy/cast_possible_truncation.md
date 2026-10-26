Pattern: Possibly truncating numeric cast

Issue: -

## Description

In some problem domains, it is good practice to avoid
truncation. This lint can be activated to help assess where additional
checks could be beneficial.

## What it does

Checks for casts between numeric types that may
truncate large values. This is expected behavior, so the cast is `Allow` by
default. It suggests user either explicitly ignore the lint,
or use `try_from()` and handle the truncation, default, or panic explicitly.

## Examples

Example of **incorrect** code:

```rust
fn as_u8(x: u64) -> u8 {
    x as u8
}
```

Example of **correct** code:

```rust
fn as_u8(x: u64) -> u8 {
    if let Ok(x) = u8::try_from(x) {
        x
    } else {
        todo!();
    }
}
// Or
#[allow(clippy::cast_possible_truncation)]
fn as_u16(x: u64) -> u16 {
    x as u16
}
```

## Further Reading

* [Clippy - cast_possible_truncation](https://clippy.rust-lang.org/stable/index.html#cast_possible_truncation)

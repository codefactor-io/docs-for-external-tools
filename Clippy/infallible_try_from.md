Pattern: Infallible `TryFrom` implementation

Issue: -

## Description

Infallible conversions should be implemented via `From` with the blanket conversion.

## What it does

Finds manual impls of `TryFrom` with infallible error types.

## Examples

Example of **incorrect** code:

```rust
use std::convert::Infallible;
struct MyStruct(i16);
impl TryFrom<i16> for MyStruct {
    type Error = Infallible;
    fn try_from(other: i16) -> Result<Self, Infallible> {
        Ok(Self(other.into()))
    }
}
```

Example of **correct** code:

```rust
struct MyStruct(i16);
impl From<i16> for MyStruct {
    fn from(other: i16) -> Self {
        Self(other)
    }
}
```

## Further Reading

* [Clippy - infallible_try_from](https://clippy.rust-lang.org/stable/index.html#infallible_try_from)

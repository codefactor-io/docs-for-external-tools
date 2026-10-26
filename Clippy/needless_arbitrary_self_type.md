Pattern: Unnecessary explicit `self` type

Issue: -

## Description

Increases the amount and decreases the readability of code

## What it does

The lint checks for `self` in fn parameters that
specify the `Self`-type explicitly

## Examples

Example of **incorrect** code:

```rust
enum ValType {
    I32,
    I64,
    F32,
    F64,
}

impl ValType {
    pub fn bytes(self: Self) -> usize {
        match self {
            Self::I32 | Self::F32 => 4,
            Self::I64 | Self::F64 => 8,
        }
    }
}
```

Example of **correct** code:

```rust
enum ValType {
    I32,
    I64,
    F32,
    F64,
}

impl ValType {
    pub fn bytes(self) -> usize {
        match self {
            Self::I32 | Self::F32 => 4,
            Self::I64 | Self::F64 => 8,
        }
    }
}
```

## Further Reading

* [Clippy - needless_arbitrary_self_type](https://clippy.rust-lang.org/stable/index.html#needless_arbitrary_self_type)

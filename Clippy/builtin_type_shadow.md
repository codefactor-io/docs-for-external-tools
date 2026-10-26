Pattern: Generic parameter shadowing built-in type

Issue: -

## Description

This gives surprising type errors.

## What it does

Warns if a generic shadows a built-in type.

## Examples

Example of **incorrect** code:

```rust
impl<u32> Foo<u32> {
    fn impl_func(&self) -> u32 {
        42
    }
}
```

## Further Reading

* [Clippy - builtin_type_shadow](https://clippy.rust-lang.org/stable/index.html#builtin_type_shadow)

Pattern: Unnecessary `PartialEq::ne()` implementation

Issue: -

## Description

`PartialEq::ne` is required to always return the
negated result of `PartialEq::eq`, which is exactly what the default
implementation does. Therefore, there should never be any need to
re-implement it.

## What it does

Checks for manual re-implementations of `PartialEq::ne`.

## Examples

Example of **incorrect** code:

```rust
struct Foo;

impl PartialEq for Foo {
    fn eq(&self, other: &Foo) -> bool { true }
    fn ne(&self, other: &Foo) -> bool { !(self == other) }
}
```

## Further Reading

* [Clippy - partialeq_ne_impl](https://clippy.rust-lang.org/stable/index.html#partialeq_ne_impl)

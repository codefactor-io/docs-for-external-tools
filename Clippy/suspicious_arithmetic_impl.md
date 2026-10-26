Pattern: Suspicious operator in arithmetic trait impl

Issue: -

## Description

This is probably a typo or copy-and-paste error and not intended.

## What it does

Lints for suspicious operations in impls of arithmetic operators, e.g.
subtracting elements in an Add impl.

## Examples

Example of **incorrect** code:

```rust
impl Add for Foo {
    type Output = Foo;

    fn add(self, other: Foo) -> Foo {
        Foo(self.0 - other.0)
    }
}
```

## Further Reading

* [Clippy - suspicious_arithmetic_impl](https://clippy.rust-lang.org/stable/index.html#suspicious_arithmetic_impl)

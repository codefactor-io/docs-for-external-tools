Pattern: Suspicious operator in `OpAssign` trait impl

Issue: -

## Description

This is probably a typo or copy-and-paste error and not intended.

## What it does

Lints for suspicious operations in impls of OpAssign, e.g.
subtracting elements in an AddAssign impl.

## Examples

Example of **incorrect** code:

```rust
impl AddAssign for Foo {
    fn add_assign(&mut self, other: Foo) {
        *self = *self - other;
    }
}
```

## Further Reading

* [Clippy - suspicious_op_assign_impl](https://clippy.rust-lang.org/stable/index.html#suspicious_op_assign_impl)

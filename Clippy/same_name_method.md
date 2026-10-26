Pattern: Inherent method with same name as trait method

Issue: -

## Description

Confusing.

## What it does

It lints if a struct has two methods with the same name:
one from a trait, another not from a trait.

## Examples

Example of **incorrect** code:

```rust
trait T {
    fn foo(&self) {}
}

struct S;

impl T for S {
    fn foo(&self) {}
}

impl S {
    fn foo(&self) {}
}
```

## Further Reading

* [Clippy - same_name_method](https://clippy.rust-lang.org/stable/index.html#same_name_method)

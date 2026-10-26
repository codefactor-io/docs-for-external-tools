Pattern: Constructor with same name as type

Issue: -

## Description

Repeating the name of the type is redundant.

## What it does

Warns when constructors have the same name as their types.

## Examples

Example of **incorrect** code:

```rust
struct Foo {}

impl Foo {
    pub fn foo() -> Foo {
        Foo {}
    }
}
```

Example of **correct** code:

```rust
struct Foo {}

impl Foo {
    pub fn new() -> Foo {
        Foo {}
    }
}
```

## Further Reading

* [Clippy - self_named_constructors](https://clippy.rust-lang.org/stable/index.html#self_named_constructors)

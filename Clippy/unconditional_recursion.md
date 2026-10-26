Pattern: Unconditional recursion in trait impl

Issue: -

## Description

Infinite recursion in trait implementation will either cause crashes
or result in an infinite loop, and it is hard to detect.

## What it does

Checks that there isn't an infinite recursion in trait
implementations.

## Examples

```rust
enum Foo {
    A,
    B,
}

impl PartialEq for Foo {
    fn eq(&self, other: &Self) -> bool {
        self == other // bad!
    }
}
```

Use instead:

```rust
#[derive(PartialEq)]
enum Foo {
    A,
    B,
}
```

As an alternative, rewrite the logic without recursion:

```rust
enum Foo {
    A,
    B,
}

impl PartialEq for Foo {
    fn eq(&self, other: &Self) -> bool {
        matches!((self, other), (Foo::A, Foo::A) | (Foo::B, Foo::B))
    }
}
```

## Further Reading

* [Clippy - unconditional_recursion](https://clippy.rust-lang.org/stable/index.html#unconditional_recursion)

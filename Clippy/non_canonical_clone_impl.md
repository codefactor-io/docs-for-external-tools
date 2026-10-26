Pattern: Non-canonical `Clone` implementation

Issue: -

## Description

If both `Clone` and `Copy` are implemented, they must agree. This can done by dereferencing
`self` in `Clone`'s implementation, which will avoid any possibility of the implementations
becoming out of sync.

## What it does

Checks for non-canonical implementations of `Clone` when `Copy` is already implemented.

## Examples

Example of **incorrect** code:

```rust
#[derive(Eq, PartialEq)]
struct A(u32);

impl Clone for A {
    fn clone(&self) -> Self {
        Self(self.0)
    }
}

impl Copy for A {}
```

Example of **correct** code:

```rust
#[derive(Eq, PartialEq)]
struct A(u32);

impl Clone for A {
    fn clone(&self) -> Self {
        *self
    }
}

impl Copy for A {}
```

## Further Reading

* [Clippy - non_canonical_clone_impl](https://clippy.rust-lang.org/stable/index.html#non_canonical_clone_impl)

Pattern: Manual `Clone` implementation on `Copy` type

Issue: -

## Description

To avoid surprising behavior, these traits should
agree and the behavior of `Copy` cannot be overridden. In almost all
situations a `Copy` type should have a `Clone` implementation that does
nothing more than copy the object, which is what `#[derive(Copy, Clone)]`
gets you.

## What it does

Checks for explicit `Clone` implementations for `Copy`
types.

## Examples

Example of **incorrect** code:

```rust
#[derive(Copy)]
struct Foo;

impl Clone for Foo {
    // ..
}
```

## Further Reading

* [Clippy - expl_impl_clone_on_copy](https://clippy.rust-lang.org/stable/index.html#expl_impl_clone_on_copy)

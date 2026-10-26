Pattern: Unused `self` parameter

Issue: -

## Description

It may be clearer to define the method as an associated function instead
of an instance method if it doesn't require `self`.

## What it does

Checks methods that contain a `self` argument but don't use it

## Examples

Example of **incorrect** code:

```rust
struct A;
impl A {
    fn method(&self) {}
}
```

Example of **correct** code:

```rust
struct A;
impl A {
    fn method() {}
}
```

## Further Reading

* [Clippy - unused_self](https://clippy.rust-lang.org/stable/index.html#unused_self)

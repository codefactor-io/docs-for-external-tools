Pattern: Missing use of `Self`

Issue: -

## Description

Unnecessary repetition. Mixed use of `Self` and struct
name
feels inconsistent.

## What it does

Checks for unnecessary repetition of structure name when a
replacement with `Self` is applicable.

## Examples

```rust
struct Foo;
impl Foo {
    fn new() -> Foo {
        Foo {}
    }
}
```
could be
```rust
struct Foo;
impl Foo {
    fn new() -> Self {
        Self {}
    }
}
```

## Known problems

- Unaddressed false negative in fn bodies of trait implementations

## Further Reading

* [Clippy - use_self](https://clippy.rust-lang.org/stable/index.html#use_self)

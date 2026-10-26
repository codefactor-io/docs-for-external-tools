Pattern: Panicking `From` implementation

Issue: -

## Description

`TryFrom` should be used if there's a possibility of failure.

## What it does

Checks for impls of `From<..>` that contain `panic!()` or `unwrap()`

## Examples

Example of **incorrect** code:

```rust
struct Foo(i32);

impl From<String> for Foo {
    fn from(s: String) -> Self {
        Foo(s.parse().unwrap())
    }
}
```

Example of **correct** code:

```rust
struct Foo(i32);

impl TryFrom<String> for Foo {
    type Error = ();
    fn try_from(s: String) -> Result<Self, Self::Error> {
        if let Ok(parsed) = s.parse() {
            Ok(Foo(parsed))
        } else {
            Err(())
        }
    }
}
```

## Further Reading

* [Clippy - fallible_impl_from](https://clippy.rust-lang.org/stable/index.html#fallible_impl_from)

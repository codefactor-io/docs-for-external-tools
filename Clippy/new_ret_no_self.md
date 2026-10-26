Pattern: `new()` not returning `Self`

Issue: -

## Description

As a convention, `new` methods are used to make a new
instance of a type.

## What it does

Checks for `new` not returning a type that contains `Self`.

## Examples

In an impl block:
```rust
impl Foo {
    fn new() -> NotAFoo {
    }
}
```

```rust
struct Bar(Foo);
impl Foo {
    // Bad. The type name must contain `Self`
    fn new() -> Bar {
    }
}
```

```rust
impl Foo {
    // Good. Return type contains `Self`
    fn new() -> Result<Foo, FooError> {
    }
}
```

Or in a trait definition:
```rust
pub trait Trait {
    // Bad. The type name must contain `Self`
    fn new();
}
```

```rust
pub trait Trait {
    // Good. Return type contains `Self`
    fn new() -> Self;
}
```

## Further Reading

* [Clippy - new_ret_no_self](https://clippy.rust-lang.org/stable/index.html#new_ret_no_self)

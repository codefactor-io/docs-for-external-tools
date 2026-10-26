Pattern: Inherent method named like `std` trait method

Issue: -

## Description

Implementing the traits improve ergonomics for users of
the code, often with very little cost. Also people seeing a `mul(...)`
method
may expect `*` to work equally, so you should have good reason to disappoint
them.

## What it does

Checks for methods that should live in a trait
implementation of a `std` trait (see [llogiq's blog
post](http://llogiq.github.io/2015/07/30/traits.html) for further
information) instead of an inherent implementation.

## Examples

Example of **incorrect** code:

```rust
struct X;
impl X {
    fn add(&self, other: &X) -> X {
        // ..
    }
}
```

## Further Reading

* [Clippy - should_implement_trait](https://clippy.rust-lang.org/stable/index.html#should_implement_trait)

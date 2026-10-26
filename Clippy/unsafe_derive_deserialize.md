Pattern: Derived `Deserialize` on type using `unsafe`

Issue: -

## Description

Deriving `serde::Deserialize` will create a constructor
that may violate invariants held by another constructor.

## What it does

Checks for deriving `serde::Deserialize` on a type that
has methods using `unsafe`.

## Examples

Example of **incorrect** code:

```rust
use serde::Deserialize;

#[derive(Deserialize)]
pub struct Foo {
    // ..
}

impl Foo {
    pub fn new() -> Self {
        // setup here ..
    }

    pub unsafe fn parts() -> (&str, &str) {
        // assumes invariants hold
    }
}
```

## Further Reading

* [Clippy - unsafe_derive_deserialize](https://clippy.rust-lang.org/stable/index.html#unsafe_derive_deserialize)

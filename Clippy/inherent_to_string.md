Pattern: Inherent `to_string()` method

Issue: -

## Description

This method is also implicitly defined if a type implements the `Display` trait. As the functionality of `Display` is much more versatile, it should be preferred.

## What it does

Checks for the definition of inherent methods with a signature of `to_string(&self) -> String`.

## Examples

Example of **incorrect** code:

```rust
pub struct A;

impl A {
    pub fn to_string(&self) -> String {
        "I am A".to_string()
    }
}
```

Example of **correct** code:

```rust
use std::fmt;

pub struct A;

impl fmt::Display for A {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "I am A")
    }
}
```

## Further Reading

* [Clippy - inherent_to_string](https://clippy.rust-lang.org/stable/index.html#inherent_to_string)

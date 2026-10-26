Pattern: Inherent `to_string()` shadowed by `Display`

Issue: -

## Description

This method is also implicitly defined if a type implements the `Display` trait. The less versatile inherent method will then shadow the implementation introduced by `Display`.

## What it does

Checks for the definition of inherent methods with a signature of `to_string(&self) -> String` and if the type implementing this method also implements the `Display` trait.

## Examples

Example of **incorrect** code:

```rust
use std::fmt;

pub struct A;

impl A {
    pub fn to_string(&self) -> String {
        "I am A".to_string()
    }
}

impl fmt::Display for A {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "I am A, too")
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

* [Clippy - inherent_to_string_shadow_display](https://clippy.rust-lang.org/stable/index.html#inherent_to_string_shadow_display)

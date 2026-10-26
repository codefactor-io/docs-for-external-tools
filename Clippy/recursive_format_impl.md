Pattern: Recursive call in format trait impl

Issue: -

## Description

This will lead to infinite recursion and a stack overflow.

## What it does

Checks for format trait implementations (e.g. `Display`) with a recursive call to itself
which uses `self` as a parameter.
This is typically done indirectly with the `write!` macro or with `to_string()`.

## Examples

Example of **incorrect** code:

```rust
use std::fmt;

struct Structure(i32);
impl fmt::Display for Structure {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "{}", self.to_string())
    }
}

```

Example of **correct** code:

```rust
use std::fmt;

struct Structure(i32);
impl fmt::Display for Structure {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "{}", self.0)
    }
}
```

## Further Reading

* [Clippy - recursive_format_impl](https://clippy.rust-lang.org/stable/index.html#recursive_format_impl)

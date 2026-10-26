Pattern: Use of `to_string()` on `&&T`

Issue: -

## Description

In versions of the compiler before Rust 1.82.0, this bypasses the specialized
implementation of `ToString` and instead goes through the more expensive string
formatting facilities.

## What it does

Checks for usage of `.to_string()` on an `&&T` where
`T` implements `ToString` directly (like `&&str` or `&&String`).

## Examples

```rust
// Generic implementation for `T: Display` is used (slow)
["foo", "bar"].iter().map(|s| s.to_string());

// OK, the specialized impl is used
["foo", "bar"].iter().map(|&s| s.to_string());
```

## Further Reading

* [Clippy - inefficient_to_string](https://clippy.rust-lang.org/stable/index.html#inefficient_to_string)

Pattern: Direct `ToString` implementation

Issue: -

## Description

This trait is automatically implemented for any type which implements the `Display` trait.
As such, `ToString` shouldn’t be implemented directly: `Display` should be implemented instead,
and you get the `ToString` implementation for free.

## What it does

Checks for direct implementations of `ToString`.

## Examples

Example of **incorrect** code:

```rust
struct Point {
  x: usize,
  y: usize,
}

impl ToString for Point {
  fn to_string(&self) -> String {
    format!("({}, {})", self.x, self.y)
  }
}
```

Example of **correct** code:

```rust
struct Point {
  x: usize,
  y: usize,
}

impl std::fmt::Display for Point {
  fn fmt(&self, f: &mut std::fmt::Formatter<'_>) -> std::fmt::Result {
    write!(f, "({}, {})", self.x, self.y)
  }
}
```

## Further Reading

* [Clippy - to_string_trait_impl](https://clippy.rust-lang.org/stable/index.html#to_string_trait_impl)

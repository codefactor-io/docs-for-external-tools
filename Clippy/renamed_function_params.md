Pattern: Renamed parameter in trait implementation

Issue: -

## Description

Using the default name for parameters of a trait method is more consistent.

## What it does

Lints when the name of function parameters from trait impl is
different than its default implementation.

## Examples

Example of **incorrect** code:

```rust
struct A(u32);

impl PartialEq for A {
    fn eq(&self, b: &Self) -> bool {
        self.0 == b.0
    }
}
```

Example of **correct** code:

```rust
struct A(u32);

impl PartialEq for A {
    fn eq(&self, other: &Self) -> bool {
        self.0 == other.0
    }
}
```

## Further Reading

* [Clippy - renamed_function_params](https://clippy.rust-lang.org/stable/index.html#renamed_function_params)

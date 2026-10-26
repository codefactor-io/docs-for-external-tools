Pattern: Repeated type in trait bounds

Issue: -

## Description

Repeating the type for every bound makes the code
less readable than combining the bounds

## What it does

This lint warns about unnecessary type repetitions in trait bounds

## Examples

Example of **incorrect** code:

```rust
pub fn foo<T>(t: T) where T: Copy, T: Clone {}
```

Example of **correct** code:

```rust
pub fn foo<T>(t: T) where T: Copy + Clone {}
```

## Further Reading

* [Clippy - type_repetition_in_bounds](https://clippy.rust-lang.org/stable/index.html#type_repetition_in_bounds)

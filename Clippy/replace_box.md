Pattern: New `Box` assigned to existing `Box<T>`

Issue: -

## Description

This incurs an extra heap allocation compared to assigning the boxed
storage.

## What it does

Detects assignments of `Default::default()` or `Box::new(value)`
to a place of type `Box<T>`.

## Examples

Example of **incorrect** code:

```rust
let mut b = Box::new(1u32);
b = Default::default();
```

Example of **correct** code:

```rust
let mut b = Box::new(1u32);
*b = Default::default();
```

## Further Reading

* [Clippy - replace_box](https://clippy.rust-lang.org/stable/index.html#replace_box)

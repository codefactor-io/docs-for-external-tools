Pattern: `reserve()` right after `Vec` creation

Issue: -

## Description

The `Vec::with_capacity` constructor is less complex.

## What it does

Informs the user about a more concise way to create a vector with a known capacity.

## Examples

Example of **incorrect** code:

```rust
let mut v: Vec<usize> = vec![];
v.reserve(10);
```

Example of **correct** code:

```rust
let mut v: Vec<usize> = Vec::with_capacity(10);
```

## Further Reading

* [Clippy - reserve_after_initialization](https://clippy.rust-lang.org/stable/index.html#reserve_after_initialization)

Pattern: Missing use of `as_chunks()`

Issue: -

## Description

`as_chunks` provides better ergonomics and type safety by returning arrays instead of slices.
It was stabilized in Rust 1.88.

## What it does

Checks for usage of `chunks_exact` or `chunks_exact_mut` with a constant chunk size.

## Examples

Example of **incorrect** code:

```rust
let slice = [1, 2, 3, 4, 5, 6];
let mut it = slice.chunks_exact(2);
for chunk in it {}
```

Example of **correct** code:

```rust
let slice = [1, 2, 3, 4, 5, 6];
let (chunks, remainder) = slice.as_chunks::<2>();
for chunk in chunks {}
```

## Further Reading

* [Clippy - chunks_exact_to_as_chunks](https://clippy.rust-lang.org/stable/index.html#chunks_exact_to_as_chunks)

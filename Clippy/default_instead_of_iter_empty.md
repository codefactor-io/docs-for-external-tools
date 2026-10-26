Pattern: Missing use of `iter::empty()`

Issue: -

## Description

`std::iter::empty()` is the more idiomatic way.

## What it does

It checks for `std::iter::Empty::default()` and suggests replacing it with
`std::iter::empty()`.

## Examples

Example of **incorrect** code:

```rust
let _ = std::iter::Empty::<usize>::default();
let iter: std::iter::Empty<usize> = std::iter::Empty::default();
```

Example of **correct** code:

```rust
let _ = std::iter::empty::<usize>();
let iter: std::iter::Empty<usize> = std::iter::empty();
```

## Further Reading

* [Clippy - default_instead_of_iter_empty](https://clippy.rust-lang.org/stable/index.html#default_instead_of_iter_empty)

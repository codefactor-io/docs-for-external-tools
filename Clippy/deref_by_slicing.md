Pattern: Slicing instead of dereferencing

Issue: -

## Description

Some people may prefer to dereference rather than slice.

## What it does

Checks for slicing expressions which are equivalent to dereferencing the
value.

## Examples

Example of **incorrect** code:

```rust
let vec = vec![1, 2, 3];
let slice = &vec[..];
```

Example of **correct** code:

```rust
let vec = vec![1, 2, 3];
let slice = &*vec;
```

## Further Reading

* [Clippy - deref_by_slicing](https://clippy.rust-lang.org/stable/index.html#deref_by_slicing)

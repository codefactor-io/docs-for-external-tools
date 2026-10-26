Pattern: Unused `peekable()` iterator

Issue: -

## Description

Creating a peekable iterator without using any of its methods is likely a mistake,
or just a leftover after a refactor.

## What it does

Checks for the creation of a `peekable` iterator that is never `.peek()`ed

## Examples

Example of **incorrect** code:

```rust
let collection = vec![1, 2, 3];
let iter = collection.iter().peekable();

for item in iter {
    // ...
}
```

Example of **correct** code:

```rust
let collection = vec![1, 2, 3];
let iter = collection.iter();

for item in iter {
    // ...
}
```

## Further Reading

* [Clippy - unused_peekable](https://clippy.rust-lang.org/stable/index.html#unused_peekable)

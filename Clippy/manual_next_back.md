Pattern: Missing use of `next_back()`

Issue: -

## Description

`.next_back()` is cleaner.

## What it does

Checks for `.rev().next()` on a `DoubleEndedIterator`

## Examples

Example of **incorrect** code:

```rust
foo.iter().rev().next();
```

Example of **correct** code:

```rust
foo.iter().next_back();
```

## Further Reading

* [Clippy - manual_next_back](https://clippy.rust-lang.org/stable/index.html#manual_next_back)

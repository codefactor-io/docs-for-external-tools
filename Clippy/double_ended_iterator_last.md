Pattern: Use of `last()` on `DoubleEndedIterator`

Issue: -

## Description

`Iterator::last` is implemented by consuming the iterator, which is unnecessary if
the iterator is a `DoubleEndedIterator`. Since Rust traits do not allow specialization,
`Iterator::last` cannot be optimized for `DoubleEndedIterator`.

## What it does

Checks for `Iterator::last` being called on a  `DoubleEndedIterator`, which can be replaced
with `DoubleEndedIterator::next_back`.

## Examples

Example of **incorrect** code:

```rust
let last_arg = "echo hello world".split(' ').last();
```

Example of **correct** code:

```rust
let last_arg = "echo hello world".split(' ').next_back();
```

## Further Reading

* [Clippy - double_ended_iterator_last](https://clippy.rust-lang.org/stable/index.html#double_ended_iterator_last)

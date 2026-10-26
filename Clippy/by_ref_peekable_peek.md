Pattern: Use of `.by_ref().peekable().peek()`

Issue: -

## Description

While it might look like this will allow peeking on the first
element of an iterator without consuming it and without consuming
the iterator itself, it will in practice consume the first element.

The implementation of `Peekable::peek()` produces the first element
of the underlying iterator, and stores it internally so that it can
be later produced. As a consequence, it advances the underlying
iterator, whose `.next()` method will now produce its second element.

## What it does

Checks for usages of `Iterator::by_ref().peekable().peek()`.

## Examples

```rust
let mut iter = [1, 2, 3].into_iter();
let x = iter.by_ref().peekable().peek();  // 1
let y = iter.by_ref().peekable().peek();  // 2
```
If this does what you intended, use the following instead, which is
shorter and clearer:
```rust
let mut iter = [1, 2, 3].into_iter();
let x = iter.next().as_ref();  // 1
let y = iter.next().as_ref();  // 2
```

## Further Reading

* [Clippy - by_ref_peekable_peek](https://clippy.rust-lang.org/stable/index.html#by_ref_peekable_peek)

Pattern: Iterator over empty collection

Issue: -

## Description

It is simpler to use the empty function from the standard library:

## What it does

Checks for calls to `iter`, `iter_mut` or `into_iter` on empty collections

## Examples

Example of **incorrect** code:

```rust
use std::{slice, option};
let a: slice::Iter<i32> = [].iter();
let f: option::IntoIter<i32> = None.into_iter();
```

Example of **correct** code:

```rust
use std::iter;
let a: iter::Empty<i32> = iter::empty();
let b: iter::Empty<i32> = iter::empty();
```

## Known problems

The type of the resulting iterator might become incompatible with its usage

## Further Reading

* [Clippy - iter_on_empty_collections](https://clippy.rust-lang.org/stable/index.html#iter_on_empty_collections)

Pattern: Iterator over single-item collection

Issue: -

## Description

It is simpler to use the once function from the standard library:

## What it does

Checks for calls to `iter`, `iter_mut` or `into_iter` on collections containing a single item

## Examples

Example of **incorrect** code:

```rust
let a = [123].iter();
let b = Some(123).into_iter();
```

Example of **correct** code:

```rust
use std::iter;
let a = iter::once(&123);
let b = iter::once(123);
```

## Known problems

The type of the resulting iterator might become incompatible with its usage

## Further Reading

* [Clippy - iter_on_single_items](https://clippy.rust-lang.org/stable/index.html#iter_on_single_items)

Pattern: Missing use of `last()`

Issue: -

## Description

Using `x.last()` is easier to read and has the same
result.

Note that using `x[x.len() - 1]` is semantically different from
`x.last()`.  Indexing into the array will panic on out-of-bounds
accesses, while `x.get()` and `x.last()` will return `None`.

There is another lint (get_unwrap) that covers the case of using
`x.get(index).unwrap()` instead of `x[index]`.

## What it does

Checks for usage of `x.get(x.len() - 1)` instead of
`x.last()`.

## Examples

Example of **incorrect** code:

```rust
let x = vec![2, 3, 5];
let last_element = x.get(x.len() - 1);
```

Example of **correct** code:

```rust
let x = vec![2, 3, 5];
let last_element = x.last();
```

## Further Reading

* [Clippy - get_last_with_len](https://clippy.rust-lang.org/stable/index.html#get_last_with_len)

Pattern: Missing use of `first()`

Issue: -

## Description

Using `x.first()` for `Vec`s and slices or `x.front()`
for `VecDeque`s is easier to read and has the same result.

## What it does

Checks for usage of `x.get(0)` instead of
`x.first()` or `x.front()`.

## Examples

Example of **incorrect** code:

```rust
let x = vec![2, 3, 5];
let first_element = x.get(0);
```

Example of **correct** code:

```rust
let x = vec![2, 3, 5];
let first_element = x.first();
```

## Further Reading

* [Clippy - get_first](https://clippy.rust-lang.org/stable/index.html#get_first)

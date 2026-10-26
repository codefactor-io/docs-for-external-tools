Pattern: Use of `filter().next()`

Issue: -

## Description

Readability, this can be written more concisely as
`_.find(_)`.

## What it does

Checks for usage of `_.filter(_).next()`.

## Examples

Example of **incorrect** code:

```rust
vec.iter().filter(|x| **x == 0).next();
```

Example of **correct** code:

```rust
vec.iter().find(|x| **x == 0);
```

## Further Reading

* [Clippy - filter_next](https://clippy.rust-lang.org/stable/index.html#filter_next)

Pattern: Search followed by `is_some()` or `is_none()`

Issue: -

## Description

Readability, this can be written more concisely as:
* `_.any(_)`, or `_.contains(_)` for `is_some()`,
* `!_.any(_)`, or `!_.contains(_)` for `is_none()`.

## What it does

Checks for an iterator or string search (such as `find()`,
`position()`, or `rposition()`) followed by a call to `is_some()` or `is_none()`.

## Examples

Example of **incorrect** code:

```rust
let vec = vec![1];
vec.iter().find(|x| **x == 0).is_some();

"hello world".find("world").is_none();
```

Example of **correct** code:

```rust
let vec = vec![1];
vec.iter().any(|x| *x == 0);

!"hello world".contains("world");
```

## Further Reading

* [Clippy - search_is_some](https://clippy.rust-lang.org/stable/index.html#search_is_some)

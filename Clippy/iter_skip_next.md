Pattern: Use of `skip(x).next()`

Issue: -

## Description

`.nth(x)` is cleaner

## What it does

Checks for usage of `.skip(x).next()` on iterators.

## Examples

Example of **incorrect** code:

```rust
let some_vec = vec![0, 1, 2, 3];
let bad_vec = some_vec.iter().skip(3).next();
let bad_slice = &some_vec[..].iter().skip(3).next();
```

Example of **correct** code:

```rust
let some_vec = vec![0, 1, 2, 3];
let bad_vec = some_vec.iter().nth(3);
let bad_slice = &some_vec[..].iter().nth(3);
```

## Further Reading

* [Clippy - iter_skip_next](https://clippy.rust-lang.org/stable/index.html#iter_skip_next)

Pattern: Use of `iter().count()` on collection

Issue: -

## Description

`.len()` is more efficient and more
readable.

## What it does

Checks for the use of `.iter().count()`.

## Examples

Example of **incorrect** code:

```rust
let some_vec = vec![0, 1, 2, 3];

some_vec.iter().count();
&some_vec[..].iter().count();
```

Example of **correct** code:

```rust
let some_vec = vec![0, 1, 2, 3];

some_vec.len();
&some_vec[..].len();
```

## Further Reading

* [Clippy - iter_count](https://clippy.rust-lang.org/stable/index.html#iter_count)

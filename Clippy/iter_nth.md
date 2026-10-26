Pattern: Use of `iter().nth()` on indexable type

Issue: -

## Description

`.get()` and `.get_mut()` are equivalent but more concise.

## What it does

Checks for usage of `.iter().nth()`/`.iter_mut().nth()` on standard library types that have
equivalent `.get()`/`.get_mut()` methods.

## Examples

Example of **incorrect** code:

```rust
let some_vec = vec![0, 1, 2, 3];
let bad_vec = some_vec.iter().nth(3);
let bad_slice = &some_vec[..].iter().nth(3);
```

Example of **correct** code:

```rust
let some_vec = vec![0, 1, 2, 3];
let bad_vec = some_vec.get(3);
let bad_slice = &some_vec[..].get(3);
```

## Further Reading

* [Clippy - iter_nth](https://clippy.rust-lang.org/stable/index.html#iter_nth)

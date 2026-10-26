Pattern: Use of `drain(..)` for iteration

Issue: -

## Description

`.into_iter()` is simpler with better performance.

## What it does

Checks for usage of `.drain(..)` on `Vec` and `VecDeque` for iteration.

## Examples

Example of **incorrect** code:

```rust
let mut foo = vec![0, 1, 2, 3];
let bar: HashSet<usize> = foo.drain(..).collect();
```

Example of **correct** code:

```rust
let foo = vec![0, 1, 2, 3];
let bar: HashSet<usize> = foo.into_iter().collect();
```

## Further Reading

* [Clippy - iter_with_drain](https://clippy.rust-lang.org/stable/index.html#iter_with_drain)

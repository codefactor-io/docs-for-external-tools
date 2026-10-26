Pattern: Missing use of `clear()`

Issue: -

## Description

This creates an unnecessary iterator that is dropped immediately.

Calling `.clear()` also makes the intent clearer.

## What it does

Checks for usage of `.drain(..)` for the sole purpose of clearing a container.

## Examples

Example of **incorrect** code:

```rust
let mut v = vec![1, 2, 3];
v.drain(..);
```

Example of **correct** code:

```rust
let mut v = vec![1, 2, 3];
v.clear();
```

## Further Reading

* [Clippy - clear_with_drain](https://clippy.rust-lang.org/stable/index.html#clear_with_drain)

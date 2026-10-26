Pattern: Missing use of `retain()`

Issue: -

## Description

`.retain()` is simpler and avoids needless allocation.

## What it does

Checks for code to be replaced by `.retain()`.

## Examples

Example of **incorrect** code:

```rust
let mut vec = vec![0, 1, 2];
vec = vec.iter().filter(|&x| x % 2 == 0).copied().collect();
vec = vec.into_iter().filter(|x| x % 2 == 0).collect();
```

Example of **correct** code:

```rust
let mut vec = vec![0, 1, 2];
vec.retain(|x| x % 2 == 0);
vec.retain(|x| x % 2 == 0);
```

## Further Reading

* [Clippy - manual_retain](https://clippy.rust-lang.org/stable/index.html#manual_retain)

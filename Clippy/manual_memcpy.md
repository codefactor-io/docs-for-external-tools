Pattern: Missing use of `copy_from_slice()`

Issue: -

## Description

It is not as fast as a memcpy.

## What it does

Checks for for-loops that manually copy items between
slices that could be optimized by having a memcpy.

## Examples

Example of **incorrect** code:

```rust
for i in 0..src.len() {
    dst[i + 64] = src[i];
}
```

Example of **correct** code:

```rust
dst[64..(src.len() + 64)].clone_from_slice(&src[..]);
```

## Further Reading

* [Clippy - manual_memcpy](https://clippy.rust-lang.org/stable/index.html#manual_memcpy)

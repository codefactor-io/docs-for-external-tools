Pattern: Incorrect swap with `a = b; b = a`

Issue: -

## Description

This looks like a failed attempt to swap.

## What it does

Checks for `foo = bar; bar = foo` sequences.

## Examples

```rust
a = b;
b = a;
```
If swapping is intended, use `swap()` instead:
```rust
std::mem::swap(&mut a, &mut b);
```

## Further Reading

* [Clippy - almost_swapped](https://clippy.rust-lang.org/stable/index.html#almost_swapped)

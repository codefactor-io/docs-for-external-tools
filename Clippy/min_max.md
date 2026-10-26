Pattern: `min()` and `max()` clamping to constant

Issue: -

## Description

This is in all probability not the intended outcome. At
the least it hurts readability of the code.

## What it does

Checks for expressions where `std::cmp::min` and `max` are
used to clamp values, but switched so that the result is constant.

## Examples

```rust
min(0, max(100, x))

// or

x.max(100).min(0)
```
It will always be equal to `0`. Probably the author meant to clamp the value
between 0 and 100, but has erroneously swapped `min` and `max`.

## Further Reading

* [Clippy - min_max](https://clippy.rust-lang.org/stable/index.html#min_max)

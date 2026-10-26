Pattern: Useless `skip(0)`

Issue: -

## Description

This was likely intended to be `.skip(1)` to skip the first element, as `.skip(0)` does
nothing. If not, the call should be removed.

## What it does

Checks for usage of `.skip(0)` on iterators.

## Examples

Example of **incorrect** code:

```rust
let v = vec![1, 2, 3];
let x = v.iter().skip(0).collect::<Vec<_>>();
let y = v.iter().collect::<Vec<_>>();
assert_eq!(x, y);
```

## Further Reading

* [Clippy - iter_skip_zero](https://clippy.rust-lang.org/stable/index.html#iter_skip_zero)

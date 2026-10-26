Pattern: Comparison of `len()` with zero

Issue: -

## Description

Some structures can answer `.is_empty()` much faster
than calculating their length. So it is good to get into the habit of using
`.is_empty()`, and having it is cheap.
Besides, it makes the intent clearer than a manual comparison in some contexts.

## What it does

Checks for getting the length of something via `.len()`
just to compare to zero, and suggests using `.is_empty()` where applicable.

## Examples

```rust
if x.len() == 0 {
    ..
}
if y.len() != 0 {
    ..
}
```
instead use
```rust
if x.is_empty() {
    ..
}
if !y.is_empty() {
    ..
}
```

## Further Reading

* [Clippy - len_zero](https://clippy.rust-lang.org/stable/index.html#len_zero)

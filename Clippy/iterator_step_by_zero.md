Pattern: Use of `step_by(0)`

Issue: -

## Description

This very much looks like an oversight. Use `panic!()` instead if you
actually intend to panic.

## What it does

Checks for calling `.step_by(0)` on iterators which panics.

## Examples

Example of **incorrect** code:

```rust
for x in (0..100).step_by(0) {
    //..
}
```

## Further Reading

* [Clippy - iterator_step_by_zero](https://clippy.rust-lang.org/stable/index.html#iterator_step_by_zero)

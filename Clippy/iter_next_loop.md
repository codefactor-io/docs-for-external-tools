Pattern: `for` loop over `next()`

Issue: -

## Description

`next()` returns either `Some(value)` if there was a
value, or `None` otherwise. The insidious thing is that `Option<_>`
implements `IntoIterator`, so that possibly one value will be iterated,
leading to some hard to find bugs. No one will want to write such code
[except to win an Underhanded Rust
Contest](https://www.reddit.com/r/rust/comments/3hb0wm/underhanded_rust_contest/cu5yuhr).

## What it does

Checks for loops on `x.next()`.

## Examples

Example of **incorrect** code:

```rust
for x in y.next() {
    ..
}
```

## Further Reading

* [Clippy - iter_next_loop](https://clippy.rust-lang.org/stable/index.html#iter_next_loop)

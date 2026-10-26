Pattern: Missing use of `repeat_n()`

Issue: -

## Description

Using `repeat_n()` is more concise and clearer. Also, `repeat_n()` is sometimes faster than `repeat().take()` when the type of the element is non-trivial to clone because the original value can be reused for the last `.next()` call rather than always cloning.

## What it does

Checks for `repeat().take()` that can be replaced with `repeat_n()`.

## Examples

Example of **incorrect** code:

```rust
let _ = std::iter::repeat(10).take(3);
```

Example of **correct** code:

```rust
let _ = std::iter::repeat_n(10, 3);
```

## Further Reading

* [Clippy - manual_repeat_n](https://clippy.rust-lang.org/stable/index.html#manual_repeat_n)

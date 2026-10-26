Pattern: `len()` without `is_empty()`

Issue: -

## Description

It is good custom to have both methods, because for
some data structures, asking about the length will be a costly operation,
whereas `.is_empty()` can usually answer in constant time. Also it used to
lead to false positives on the [`len_zero`](#len_zero) lint – currently that
lint will ignore such entities.

## What it does

Checks for items that implement `.len()` but not
`.is_empty()`.

## Examples

Example of **incorrect** code:

```rust
impl X {
    pub fn len(&self) -> usize {
        ..
    }
}
```

## Further Reading

* [Clippy - len_without_is_empty](https://clippy.rust-lang.org/stable/index.html#len_without_is_empty)

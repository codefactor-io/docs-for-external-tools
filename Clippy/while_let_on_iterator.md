Pattern: Use of `while let` on iterator

Issue: -

## Description

Readability. A simple `for` loop is shorter and conveys
the intent better.

## What it does

Checks for `while let` expressions on iterators.

## Examples

Example of **incorrect** code:

```rust
while let Some(val) = iter.next() {
    ..
}
```

Example of **correct** code:

```rust
for val in &mut iter {
    ..
}
```

## Further Reading

* [Clippy - while_let_on_iterator](https://clippy.rust-lang.org/stable/index.html#while_let_on_iterator)

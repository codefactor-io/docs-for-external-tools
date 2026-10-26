Pattern: Missing `return` statement

Issue: -

## Description

Omitting the return keyword whenever possible is idiomatic Rust code, but:

* Programmers coming from other languages might prefer the expressiveness of `return`.
* It's possible to miss the last returning statement because the only difference is a missing `;`.
* Especially in bigger code with multiple return paths, having a `return` keyword makes it easier to find the
  corresponding statements.

## What it does

Checks for missing return statements at the end of a block.

## Examples

```rust
fn foo(x: usize) -> usize {
    x
}
```
add return
```rust
fn foo(x: usize) -> usize {
    return x;
}
```

## Further Reading

* [Clippy - implicit_return](https://clippy.rust-lang.org/stable/index.html#implicit_return)

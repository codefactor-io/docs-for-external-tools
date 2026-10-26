Pattern: Unnecessary `return`

Issue: -

## Description

Removing the `return` and semicolon will make the code
more rusty.

## What it does

Checks for return statements at the end of a block.

## Examples

```rust
fn foo(x: usize) -> usize {
    return x;
}
```
simplify to
```rust
fn foo(x: usize) -> usize {
    x
}
```

## Further Reading

* [Clippy - needless_return](https://clippy.rust-lang.org/stable/index.html#needless_return)

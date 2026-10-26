Pattern: Unnecessary `Box<T>` for local value

Issue: -

## Description

This is an unnecessary allocation, and bad for
performance. It is only necessary to allocate if you wish to move the box
into something.

## What it does

Checks for usage of `Box<T>` where an unboxed `T` would
work fine.

## Examples

Example of **incorrect** code:

```rust
fn foo(x: Box<u32>) {}
```

Example of **correct** code:

```rust
fn foo(x: u32) {}
```

## Further Reading

* [Clippy - boxed_local](https://clippy.rust-lang.org/stable/index.html#boxed_local)

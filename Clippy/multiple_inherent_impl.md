Pattern: Multiple inherent `impl` blocks

Issue: -

## Description

Splitting the implementation of a type makes the code harder to navigate.

## What it does

Checks for multiple inherent implementations of a struct

The config option controls the scope in which multiple inherent `impl` blocks for the same
struct are linted, allowing values of `module` (only within the same module), `file`
(within the same file), or `crate` (anywhere in the crate, default).

## Examples

Example of **incorrect** code:

```rust
struct X;
impl X {
    fn one() {}
}
impl X {
    fn other() {}
}
```

Example of **correct** code:

```rust
struct X;
impl X {
    fn one() {}
    fn other() {}
}
```

## Further Reading

* [Clippy - multiple_inherent_impl](https://clippy.rust-lang.org/stable/index.html#multiple_inherent_impl)

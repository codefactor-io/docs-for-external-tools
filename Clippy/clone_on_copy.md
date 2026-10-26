Pattern: Unnecessary `clone()` on `Copy` type

Issue: -

## Description

The only reason `Copy` types implement `Clone` is for
generics, not for using the `clone` method on a concrete type.

## What it does

Checks for usage of `.clone()` on a `Copy` type.

## Examples

Example of **incorrect** code:

```rust
42u64.clone();
```

## Further Reading

* [Clippy - clone_on_copy](https://clippy.rust-lang.org/stable/index.html#clone_on_copy)

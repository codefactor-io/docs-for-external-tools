Pattern: Unnecessary `pub(self)` visibility

Issue: -

## Description

It's unnecessary, omitting the `pub` entirely will give the same results.

## What it does

Checks for usage of `pub(self)` and `pub(in self)`.

## Examples

Example of **incorrect** code:

```rust
pub(self) type OptBox<T> = Option<Box<T>>;
```

Example of **correct** code:

```rust
type OptBox<T> = Option<Box<T>>;
```

## Further Reading

* [Clippy - needless_pub_self](https://clippy.rust-lang.org/stable/index.html#needless_pub_self)

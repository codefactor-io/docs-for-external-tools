Pattern: Use of `pub(<loc>)` without `in`

Issue: -

## Description

Consistency. Use it or don't, just be consistent about it.

Also see the `pub_without_shorthand` lint for an alternative.

## What it does

Checks for usage of `pub(<loc>)` with `in`.

## Examples

Example of **incorrect** code:

```rust
pub(super) type OptBox<T> = Option<Box<T>>;
```

Example of **correct** code:

```rust
pub(in super) type OptBox<T> = Option<Box<T>>;
```

## Further Reading

* [Clippy - pub_with_shorthand](https://clippy.rust-lang.org/stable/index.html#pub_with_shorthand)

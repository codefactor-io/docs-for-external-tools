Pattern: Use of `pub(in <loc>)`

Issue: -

## Description

Consistency. Use it or don't, just be consistent about it.

Also see the `pub_with_shorthand` lint for an alternative.

## What it does

Checks for usage of `pub(<loc>)` without `in`.

Note: As you cannot write a module's path in `pub(<loc>)`, this will only trigger on
`pub(super)` and the like.

## Examples

Example of **incorrect** code:

```rust
pub(in super) type OptBox<T> = Option<Box<T>>;
```

Example of **correct** code:

```rust
pub(super) type OptBox<T> = Option<Box<T>>;
```

## Further Reading

* [Clippy - pub_without_shorthand](https://clippy.rust-lang.org/stable/index.html#pub_without_shorthand)

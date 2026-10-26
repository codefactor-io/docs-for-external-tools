Pattern: Use of `cloned()` instead of `copied()`

Issue: -

## Description

`copied()` is better because it guarantees that the type being cloned
implements `Copy`.

## What it does

Checks for usage of `cloned()` on an `Iterator` or `Option` where
`copied()` could be used instead.

## Examples

Example of **incorrect** code:

```rust
[1, 2, 3].iter().cloned();
```

Example of **correct** code:

```rust
[1, 2, 3].iter().copied();
```

## Further Reading

* [Clippy - cloned_instead_of_copied](https://clippy.rust-lang.org/stable/index.html#cloned_instead_of_copied)

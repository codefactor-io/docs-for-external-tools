Pattern: Use of `into_iter()` on reference

Issue: -

## Description

Readability. Calling `into_iter` on a reference will not move out its
content into the resulting iterator, which is confusing. It is better just call `iter` or
`iter_mut` directly.

## What it does

Checks for `into_iter` calls on references which should be replaced by `iter`
or `iter_mut`.

## Examples

Example of **incorrect** code:

```rust
(&vec).into_iter();
```

Example of **correct** code:

```rust
(&vec).iter();
```

## Further Reading

* [Clippy - into_iter_on_ref](https://clippy.rust-lang.org/stable/index.html#into_iter_on_ref)

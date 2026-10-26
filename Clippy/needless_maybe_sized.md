Pattern: Unnecessary `?Sized` bound

Issue: -

## Description

The `?Sized` bound is misleading because it cannot be satisfied by an
unsized type

## What it does

Lints `?Sized` bounds applied to type parameters that cannot be unsized

## Examples

Example of **incorrect** code:

```rust
// `T` cannot be unsized because `Clone` requires it to be `Sized`
fn f<T: Clone + ?Sized>(t: &T) {}
```

Example of **correct** code:

```rust
fn f<T: Clone>(t: &T) {}

// or choose alternative bounds for `T` so that it can be unsized
```

## Further Reading

* [Clippy - needless_maybe_sized](https://clippy.rust-lang.org/stable/index.html#needless_maybe_sized)

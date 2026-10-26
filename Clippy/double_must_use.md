Pattern: Redundant `#[must_use]` for `#[must_use]` type

Issue: -

## Description

The attribute isn't needed. Not using the result
will already be reported. Alternatively, one can add some text to the
attribute to improve the lint message.

## What it does

Checks for a `#[must_use]` attribute without
further information on functions and methods that return a type already
considered as `#[must_use]`.

## Examples

Example of **incorrect** code:

```rust
#[must_use]
fn double_must_use() -> Result<(), ()> {
    unimplemented!();
}
```

## Note

The compiler may consider a type as being indirectly `#[must_use]`. For
example, although `Box<_>` itself is not `#[must_use]`, `Box<T>` will be
considered `#[must_use]` if `T` is.
```rust

## Further Reading

* [Clippy - double_must_use](https://clippy.rust-lang.org/stable/index.html#double_must_use)

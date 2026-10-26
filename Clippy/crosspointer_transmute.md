Pattern: Transmute between type and pointer to it

Issue: -

## Description

It's easy to mistakenly transmute between a type and a
pointer to that type.

## What it does

Checks for transmutes between a type `T` and `*T`.

## Examples

Example of **incorrect** code:

```rust
core::intrinsics::transmute(t) // where the result type is the same as
                               // `*t` or `&t`'s
```

## Further Reading

* [Clippy - crosspointer_transmute](https://clippy.rust-lang.org/stable/index.html#crosspointer_transmute)

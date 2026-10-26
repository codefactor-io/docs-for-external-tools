Pattern: Derived `Hash` with manual `PartialEq`

Issue: -

## Description

The implementation of these traits must agree (for
example for use with `HashMap`) so it’s probably a bad idea to use a
default-generated `Hash` implementation with an explicitly defined
`PartialEq`. In particular, the following must hold for any type:

```text
k1 == k2 ⇒ hash(k1) == hash(k2)
```

## What it does

Lints against manual `PartialEq` implementations for types with a derived `Hash`
implementation.

## Examples

Example of **incorrect** code:

```rust
#[derive(Hash)]
struct Foo;

impl PartialEq for Foo {
    ...
}
```

## Further Reading

* [Clippy - derived_hash_with_manual_eq](https://clippy.rust-lang.org/stable/index.html#derived_hash_with_manual_eq)

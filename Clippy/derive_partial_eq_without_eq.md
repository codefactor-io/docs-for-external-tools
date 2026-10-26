Pattern: Derived `PartialEq` without `Eq`

Issue: -

## Description

If a type `T` derives `PartialEq` and all of its members implement `Eq`,
then `T` can always implement `Eq`. Implementing `Eq` allows `T` to be used
in APIs that require `Eq` types. It also allows structs containing `T` to derive
`Eq` themselves.

## What it does

Checks for types that derive `PartialEq` and could implement `Eq`.

## Examples

Example of **incorrect** code:

```rust
#[derive(PartialEq)]
struct Foo {
    i_am_eq: i32,
    i_am_eq_too: Vec<String>,
}
```

Example of **correct** code:

```rust
#[derive(PartialEq, Eq)]
struct Foo {
    i_am_eq: i32,
    i_am_eq_too: Vec<String>,
}
```

## Further Reading

* [Clippy - derive_partial_eq_without_eq](https://clippy.rust-lang.org/stable/index.html#derive_partial_eq_without_eq)

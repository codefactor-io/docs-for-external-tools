Pattern: Inconsistent type parameter order in `impl`

Issue: -

## Description

Type parameters are determined by their position rather than name.
Naming type parameters inconsistently may cause you to refer to the
wrong type parameter.

## What it does

Checks for type parameters which are positioned inconsistently between
a type definition and impl block. Specifically, a parameter in an impl
block which has the same name as a parameter in the type def, but is in
a different place.

## Examples

Example of **incorrect** code:

```rust
struct Foo<A, B> {
    x: A,
    y: B,
}
// inside the impl, B refers to Foo::A
impl<B, A> Foo<B, A> {}
```

Example of **correct** code:

```rust
struct Foo<A, B> {
    x: A,
    y: B,
}
impl<A, B> Foo<A, B> {}
```

## Limitations

This lint only applies to impl blocks with simple generic params, e.g.
`A`. If there is anything more complicated, such as a tuple, it will be
ignored.

## Further Reading

* [Clippy - mismatching_type_param_order](https://clippy.rust-lang.org/stable/index.html#mismatching_type_param_order)

Pattern: Exported enum without `#[non_exhaustive]`

Issue: -

## Description

Making an `enum` exhaustive is a stability commitment: adding a variant is a breaking change.
A project may wish to ensure that there are no exhaustive enums or that every exhaustive
`enum` is explicitly `#[allow]`ed.

## What it does

Warns on any exported `enum`s that are not tagged `#[non_exhaustive]`

## Examples

Example of **incorrect** code:

```rust
enum Foo {
    Bar,
    Baz
}
```

Example of **correct** code:

```rust
#[non_exhaustive]
enum Foo {
    Bar,
    Baz
}
```

## Further Reading

* [Clippy - exhaustive_enums](https://clippy.rust-lang.org/stable/index.html#exhaustive_enums)

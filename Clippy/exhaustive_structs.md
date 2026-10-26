Pattern: Exported struct without `#[non_exhaustive]`

Issue: -

## Description

Making a `struct` exhaustive is a stability commitment: adding a field is a breaking change.
A project may wish to ensure that there are no exhaustive structs or that every exhaustive
`struct` is explicitly `#[allow]`ed.

## What it does

Warns on any exported `struct`s that are not tagged `#[non_exhaustive]`

## Examples

Example of **incorrect** code:

```rust
struct Foo {
    bar: u8,
    baz: String,
}
```

Example of **correct** code:

```rust
#[non_exhaustive]
struct Foo {
    bar: u8,
    baz: String,
}
```

## Further Reading

* [Clippy - exhaustive_structs](https://clippy.rust-lang.org/stable/index.html#exhaustive_structs)

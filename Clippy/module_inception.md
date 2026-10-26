Pattern: Module with same name as parent module

Issue: -

## Description

A typical beginner mistake is to have `mod foo;` and
again `mod foo { ..
}` in `foo.rs`.
The expectation is that items inside the inner `mod foo { .. }` are then
available
through `foo::x`, but they are only available through
`foo::foo::x`.
If this is done on purpose, it would be better to choose a more
representative module name.

## What it does

Checks for modules that have the same name as their
parent module

## Examples

Example of **incorrect** code:

```rust
// lib.rs
mod foo;
// foo.rs
mod foo {
    ...
}
```

## Further Reading

* [Clippy - module_inception](https://clippy.rust-lang.org/stable/index.html#module_inception)

Pattern: Unused type parameter

Issue: -

## Description

Functions cannot infer the value of unused type parameters; therefore, calling them
requires using a turbofish, which serves no purpose but to satisfy the compiler.

## What it does

Checks for type parameters in generics that are never used anywhere else.

## Examples

Example of **incorrect** code:

```rust
fn unused_ty<T>(x: u8) {
    // ..
}
```

Example of **correct** code:

```rust
fn no_unused_ty(x: u8) {
    // ..
}
```

## Further Reading

* [Clippy - extra_unused_type_parameters](https://clippy.rust-lang.org/stable/index.html#extra_unused_type_parameters)

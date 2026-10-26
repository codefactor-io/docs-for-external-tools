Pattern: Inconsistent macro braces

Issue: -

## Description

Having non-conventional braces on well-stablished macros can be confusing
when debugging, and they bring incosistencies with the rest of the ecosystem.

## What it does

Checks that common macros are used with consistent bracing.

## Examples

Example of **incorrect** code:

```rust
vec!{1, 2, 3};
```

Example of **correct** code:

```rust
vec![1, 2, 3];
```

## Further Reading

* [Clippy - nonstandard_macro_braces](https://clippy.rust-lang.org/stable/index.html#nonstandard_macro_braces)

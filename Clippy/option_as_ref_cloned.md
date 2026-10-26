Pattern: Use of `as_ref().cloned()` on `Option`

Issue: -

## Description

This can be written more concisely by cloning the `Option` directly.

## What it does

Checks for usage of `.as_ref().cloned()` and `.as_mut().cloned()` on `Option`s

## Examples

Example of **incorrect** code:

```rust
fn foo(bar: &Option<Vec<u8>>) -> Option<Vec<u8>> {
    bar.as_ref().cloned()
}
```

Example of **correct** code:

```rust
fn foo(bar: &Option<Vec<u8>>) -> Option<Vec<u8>> {
    bar.clone()
}
```

## Further Reading

* [Clippy - option_as_ref_cloned](https://clippy.rust-lang.org/stable/index.html#option_as_ref_cloned)

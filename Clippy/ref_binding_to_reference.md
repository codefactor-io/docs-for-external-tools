Pattern: `ref` binding to reference

Issue: -

## Description

The address-of operator at the use site is clearer about the need for a reference.

## What it does

Checks for `ref` bindings which create a reference to a reference.

## Examples

Example of **incorrect** code:

```rust
let x = Some("");
if let Some(ref x) = x {
    // use `x` here
}
```

Example of **correct** code:

```rust
let x = Some("");
if let Some(x) = x {
    // use `&x` here
}
```

## Further Reading

* [Clippy - ref_binding_to_reference](https://clippy.rust-lang.org/stable/index.html#ref_binding_to_reference)

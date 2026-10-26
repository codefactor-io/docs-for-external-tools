Pattern: Binding shadowed by itself

Issue: -

## Description

To require that what are formally distinct variables be given distinct names.

See also `shadow_reuse` and `shadow_unrelated` for other restrictions on shadowing.

## What it does

Checks for bindings that shadow other bindings already in
scope, while just changing reference level or mutability.

## Examples

Example of **incorrect** code:

```rust
let x = &x;
```

Example of **correct** code:

```rust
let y = &x; // use different variable name
```

## Further Reading

* [Clippy - shadow_same](https://clippy.rust-lang.org/stable/index.html#shadow_same)

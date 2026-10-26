Pattern: Shadowed binding with unrelated value

Issue: -

## Description

Shadowing a binding with a closely related one is part of idiomatic Rust,
but shadowing a binding by accident with an unrelated one may indicate a mistake.

Additionally, name shadowing in general can hurt readability, especially in
large code bases, because it is easy to lose track of the active binding at
any place in the code. If linting against all shadowing is desired, you may wish
to use the `shadow_same` and `shadow_reuse` lints as well.

## What it does

Checks for bindings that shadow other bindings already in
scope, either without an initialization or with one that does not even use
the original value.

## Examples

Example of **incorrect** code:

```rust
let x = y;
let x = z; // shadows the earlier binding
```

Example of **correct** code:

```rust
let x = y;
let w = z; // use different variable name
```

## Further Reading

* [Clippy - shadow_unrelated](https://clippy.rust-lang.org/stable/index.html#shadow_unrelated)

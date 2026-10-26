Pattern: Use of `?` operator

Issue: -

## Description

Sometimes code wants to avoid the `?` operator because for instance a local
block requires a macro to re-throw errors to attach additional information to the
error.

## What it does

Checks for expressions that use the `?` operator and rejects them.

## Examples

Example of **incorrect** code:

```rust
let result = expr?;
```

Example of **correct** code:

```rust
utility_macro!(expr);
```

## Further Reading

* [Clippy - question_mark_used](https://clippy.rust-lang.org/stable/index.html#question_mark_used)

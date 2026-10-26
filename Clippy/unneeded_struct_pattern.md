Pattern: Struct pattern on unit variant

Issue: -

## Description

Struct pattern `{ }` or `{ .. }` is not needed for unit variant.

## What it does

Checks for struct patterns that match against unit variant.

## Examples

Example of **incorrect** code:

```rust
match Some(42) {
    Some(v) => v,
    None { .. } => 0,
};
// Or
match Some(42) {
    Some(v) => v,
    None { } => 0,
};
```

Example of **correct** code:

```rust
match Some(42) {
    Some(v) => v,
    None => 0,
};
```

## Further Reading

* [Clippy - unneeded_struct_pattern](https://clippy.rust-lang.org/stable/index.html#unneeded_struct_pattern)

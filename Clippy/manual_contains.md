Pattern: Missing use of slice `contains()`

Issue: -

## Description

`contains()` is more concise and idiomatic, while also being faster in some cases.

## What it does

Checks for usage of `iter().any()` on slices when it can be replaced with `contains()` and suggests doing so.

## Examples

Example of **incorrect** code:

```rust
fn foo(values: &[u8]) -> bool {
    values.iter().any(|&v| v == 10)
}
```

Example of **correct** code:

```rust
fn foo(values: &[u8]) -> bool {
    values.contains(&10)
}
```

## Further Reading

* [Clippy - manual_contains](https://clippy.rust-lang.org/stable/index.html#manual_contains)

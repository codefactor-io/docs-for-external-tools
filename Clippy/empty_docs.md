Pattern: Empty documentation

Issue: -

## Description

Empty docs clutter code without adding value, reducing readability and maintainability.

## What it does

Detects documentation that is empty.

## Examples

Example of **incorrect** code:

```rust
///
fn returns_true() -> bool {
    true
}
```

Example of **correct** code:

```rust
fn returns_true() -> bool {
    true
}
```

## Further Reading

* [Clippy - empty_docs](https://clippy.rust-lang.org/stable/index.html#empty_docs)

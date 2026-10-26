Pattern: Empty `Drop` implementation

Issue: -

## Description

Empty `Drop` implementations have no effect when dropping an instance of the type. They are
most likely useless. However, an empty `Drop` implementation prevents a type from being
destructured, which might be the intention behind adding the implementation as a marker.

## What it does

Checks for empty `Drop` implementations.

## Examples

Example of **incorrect** code:

```rust
struct S;

impl Drop for S {
    fn drop(&mut self) {}
}
```

Example of **correct** code:

```rust
struct S;
```

## Further Reading

* [Clippy - empty_drop](https://clippy.rust-lang.org/stable/index.html#empty_drop)

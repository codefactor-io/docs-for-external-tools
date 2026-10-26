Pattern: Duplicate attribute

Issue: -

## Description

Repeating an attribute on the same item (or globally on the same crate)
is unnecessary and doesn't have an effect.

## What it does

Checks for attributes that appear two or more times.

## Examples

Example of **incorrect** code:

```rust
#[allow(dead_code)]
#[allow(dead_code)]
fn foo() {}
```

Example of **correct** code:

```rust
#[allow(dead_code)]
fn foo() {}
```

## Further Reading

* [Clippy - duplicated_attributes](https://clippy.rust-lang.org/stable/index.html#duplicated_attributes)

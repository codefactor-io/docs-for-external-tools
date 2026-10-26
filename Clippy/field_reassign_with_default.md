Pattern: Field assignment after `Default::default()`

Issue: -

## Description

It's more idiomatic to use the [functional update syntax](https://doc.rust-lang.org/reference/expressions/struct-expr.html#functional-update-syntax).

## What it does

Checks for immediate reassignment of fields initialized
with Default::default().

## Examples

Example of **incorrect** code:

```rust
let mut a: A = Default::default();
a.i = 42;
```

Example of **correct** code:

```rust
let a = A {
    i: 42,
    .. Default::default()
};
```

## Known problems

Assignments to patterns that are of tuple type are not linted.

## Further Reading

* [Clippy - field_reassign_with_default](https://clippy.rust-lang.org/stable/index.html#field_reassign_with_default)

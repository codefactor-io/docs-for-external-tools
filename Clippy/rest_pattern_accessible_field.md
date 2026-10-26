Pattern: Use of `..` for accessible fields

Issue: -

## Description

It might lead to unhandled fields when the struct changes.

## What it does

Disallow the use of rest patterns for accessible fields

## Examples

Example of **incorrect** code:

```rust
struct S {
    a: u8,
    b: u8,
    c: u8,
}

let s = S { a: 1, b: 2, c: 3 };

let S { a, b, .. } = s;
```

Example of **correct** code:

```rust
struct S {
    a: u8,
    b: u8,
    c: u8,
}

let s = S { a: 1, b: 2, c: 3 };

let S { a, b, c: _ } = s;
```

## Further Reading

* [Clippy - rest_pattern_accessible_field](https://clippy.rust-lang.org/stable/index.html#rest_pattern_accessible_field)

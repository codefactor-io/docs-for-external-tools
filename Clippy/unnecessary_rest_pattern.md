Pattern: Unnecessary rest pattern `..`

Issue: -

## Description

It might lead to unhandled fields when the struct changes.

## What it does

Disallow the use of rest patterns that don't capture any fields.

## Examples

Example of **incorrect** code:

```rust
struct S {
    a: u8,
    b: u8,
    c: u8,
}

let s = S { a: 1, b: 2, c: 3 };

let S { a, b, c, .. } = s;
```

Example of **correct** code:

```rust
struct S {
    a: u8,
    b: u8,
    c: u8,
}

let s = S { a: 1, b: 2, c: 3 };

let S { a, b, c } = s;
```

## Further Reading

* [Clippy - unnecessary_rest_pattern](https://clippy.rust-lang.org/stable/index.html#unnecessary_rest_pattern)

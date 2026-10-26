Pattern: All `match` arms prefixed with `&`

Issue: -

## Description

It just makes the code less readable. That reference
destructuring adds nothing to the code.

## What it does

Checks for matches where all arms match a reference,
suggesting to remove the reference and deref the matched expression
instead. It also checks for `if let &foo = bar` blocks.

## Examples

Example of **incorrect** code:

```rust
match x {
    &A(ref y) => foo(y),
    &B => bar(),
    _ => frob(&x),
}
```

Example of **correct** code:

```rust
match *x {
    A(ref y) => foo(y),
    B => bar(),
    _ => frob(x),
}
```

## Further Reading

* [Clippy - match_ref_pats](https://clippy.rust-lang.org/stable/index.html#match_ref_pats)

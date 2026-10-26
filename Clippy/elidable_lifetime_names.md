Pattern: Named lifetime replaceable with `'_`

Issue: -

## Description

The additional lifetimes can make the code look more complicated.

## What it does

Checks for lifetime annotations which can be replaced with anonymous lifetimes (`'_`).

## Examples

Example of **incorrect** code:

```rust
fn f<'a>(x: &'a str) -> Chars<'a> {
    x.chars()
}
```

Example of **correct** code:

```rust
fn f(x: &str) -> Chars<'_> {
    x.chars()
}
```

## Known problems

This lint ignores functions with `where` clauses that reference
lifetimes to prevent false positives.

## Further Reading

* [Clippy - elidable_lifetime_names](https://clippy.rust-lang.org/stable/index.html#elidable_lifetime_names)

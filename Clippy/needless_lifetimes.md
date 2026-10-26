Pattern: Unnecessary explicit lifetimes

Issue: -

## Description

The additional lifetimes make the code look more
complicated, while there is nothing out of the ordinary going on. Removing
them leads to more readable code.

## What it does

Checks for lifetime annotations which can be removed by
relying on lifetime elision.

## Examples

Example of **incorrect** code:

```rust
// Unnecessary lifetime annotations
fn in_and_out<'a>(x: &'a u8, y: u8) -> &'a u8 {
    x
}
```

Example of **correct** code:

```rust
fn elided(x: &u8, y: u8) -> &u8 {
    x
}
```

## Known problems

This lint ignores functions with `where` clauses that reference
lifetimes to prevent false positives.

## Further Reading

* [Clippy - needless_lifetimes](https://clippy.rust-lang.org/stable/index.html#needless_lifetimes)

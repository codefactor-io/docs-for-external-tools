Pattern: Comparison chain instead of `match` on `cmp()`

Issue: -

## Description

`if` is not guaranteed to be exhaustive and conditionals can get
repetitive

## What it does

Checks comparison chains written with `if` that can be
rewritten with `match` and `cmp`.

## Examples

Example of **incorrect** code:

```rust
fn f(x: u8, y: u8) {
    if x > y {
        a()
    } else if x < y {
        b()
    } else {
        c()
    }
}
```

Example of **correct** code:

```rust
use std::cmp::Ordering;
fn f(x: u8, y: u8) {
     match x.cmp(&y) {
         Ordering::Greater => a(),
         Ordering::Less => b(),
         Ordering::Equal => c()
     }
}
```

## Further Reading

* [Clippy - comparison_chain](https://clippy.rust-lang.org/stable/index.html#comparison_chain)

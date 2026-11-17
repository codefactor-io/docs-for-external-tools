Pattern: Unnecessary `fold()`

Issue: -

## Description

Readability.

## What it does

Checks for usage of `fold` when a more succinct alternative exists.
Specifically, this checks for `fold`s which could be replaced by `any`, `all`,
`sum` or `product`, and for folds over an `Option`'s iterator which could be
replaced by `map_or`.

## Examples

Example of **incorrect** code:

```rust
(0..3).fold(false, |acc, x| acc || x > 2);
opt.iter().fold(0, |acc, x| acc | x);
```

Example of **correct** code:

```rust
(0..3).any(|x| x > 2);
opt.as_ref().map_or(0, |x| 0 | x);
```

## Further Reading

* [Clippy - unnecessary_fold](https://clippy.rust-lang.org/stable/index.html#unnecessary_fold)

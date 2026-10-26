Pattern: Unnecessary `fold()`

Issue: -

## Description

Readability.

## What it does

Checks for usage of `fold` when a more succinct alternative exists.
Specifically, this checks for `fold`s which could be replaced by `any`, `all`,
`sum` or `product`.

## Examples

Example of **incorrect** code:

```rust
(0..3).fold(false, |acc, x| acc || x > 2);
```

Example of **correct** code:

```rust
(0..3).any(|x| x > 2);
```

## Further Reading

* [Clippy - unnecessary_fold](https://clippy.rust-lang.org/stable/index.html#unnecessary_fold)

Pattern: Use of `Some(x).filter()`

Issue: -

## Description

Readability, this can be written more concisely as `predicate.then_some(x)`.

## What it does

Checks for usage of `Some(x).filter(|_| predicate)`.

## Examples

Example of **incorrect** code:

```rust
let x = false;
Some(0).filter(|_| x);
```

Example of **correct** code:

```rust
let x = false;
x.then_some(0);
```

## Further Reading

* [Clippy - some_filter](https://clippy.rust-lang.org/stable/index.html#some_filter)

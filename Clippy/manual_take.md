Pattern: Missing use of `mem::take()`

Issue: -

## Description

Because the function call is shorter and easier to read.

## What it does

Detects manual re-implementations of `std::mem::take`.

## Examples

Example of **incorrect** code:

```rust
let mut x = true;
let _ = if x {
    x = false;
    true
} else {
    false
};
```

Example of **correct** code:

```rust
let mut x = true;
let _ = std::mem::take(&mut x);
```

## Known issues

Currently the lint only detects cases involving `bool`s.

## Further Reading

* [Clippy - manual_take](https://clippy.rust-lang.org/stable/index.html#manual_take)

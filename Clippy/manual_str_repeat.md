Pattern: Missing use of `str::repeat()`

Issue: -

## Description

These are both harder to read, as well as less performant.

## What it does

Checks for manual implementations of `str::repeat`

## Examples

Example of **incorrect** code:

```rust
let x: String = std::iter::repeat('x').take(10).collect();
```

Example of **correct** code:

```rust
let x: String = "x".repeat(10);
```

## Further Reading

* [Clippy - manual_str_repeat](https://clippy.rust-lang.org/stable/index.html#manual_str_repeat)

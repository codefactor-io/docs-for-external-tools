Pattern: Impossible double comparison

Issue: -

## Description

The whole expression can be replaced by `false`,
which is probably not the programmer's intention

## What it does

Checks for double comparisons that can never succeed

## Examples

Example of **incorrect** code:

```rust
if status_code <= 400 && status_code > 500 {}
```

## Further Reading

* [Clippy - impossible_comparisons](https://clippy.rust-lang.org/stable/index.html#impossible_comparisons)

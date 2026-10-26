Pattern: Use of `unreachable!`

Issue: -

## Description

This macro, or panics in general, may be unwanted in production code.

## What it does

Checks for usage of `unreachable!`.

## Examples

Example of **incorrect** code:

```rust
unreachable!();
```

## Further Reading

* [Clippy - unreachable](https://clippy.rust-lang.org/stable/index.html#unreachable)

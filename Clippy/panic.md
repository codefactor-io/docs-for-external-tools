Pattern: Use of `panic!`

Issue: -

## Description

This macro, or panics in general, may be unwanted in production code.

## What it does

Checks for usage of `panic!`.

## Examples

Example of **incorrect** code:

```rust
panic!("even with a good reason");
```

## Further Reading

* [Clippy - panic](https://clippy.rust-lang.org/stable/index.html#panic)

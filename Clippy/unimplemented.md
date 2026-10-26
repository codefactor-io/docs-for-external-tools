Pattern: Use of `unimplemented!`

Issue: -

## Description

This macro, or panics in general, may be unwanted in production code.

## What it does

Checks for usage of `unimplemented!`.

## Examples

Example of **incorrect** code:

```rust
unimplemented!();
```

## Further Reading

* [Clippy - unimplemented](https://clippy.rust-lang.org/stable/index.html#unimplemented)

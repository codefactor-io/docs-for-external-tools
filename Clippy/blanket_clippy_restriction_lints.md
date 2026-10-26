Pattern: Whole restriction group enabled

Issue: -

## Description

Restriction lints sometimes are in contrast with other lints or even go against idiomatic rust.
These lints should only be enabled on a lint-by-lint basis and with careful consideration.

## What it does

Checks for `warn`/`deny`/`forbid` attributes targeting the whole clippy::restriction category.

## Examples

Example of **incorrect** code:

```rust
#![deny(clippy::restriction)]
```

Example of **correct** code:

```rust
#![deny(clippy::as_conversions)]
```

## Further Reading

* [Clippy - blanket_clippy_restriction_lints](https://clippy.rust-lang.org/stable/index.html#blanket_clippy_restriction_lints)

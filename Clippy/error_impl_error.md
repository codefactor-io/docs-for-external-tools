Pattern: Public type `Error` implementing `Error`

Issue: -

## Description

It can become confusing when a codebase has 20 types all named `Error`, requiring either
aliasing them in the `use` statement or qualifying them like `my_module::Error`. This
hinders comprehension, as it requires you to memorize every variation of importing `Error`
used across a codebase.

## What it does

Checks for types named `Error` that implement `Error`.

## Examples

Example of **incorrect** code:

```rust
#[derive(Debug)]
pub enum Error { ... }

impl std::fmt::Display for Error { ... }

impl std::error::Error for Error { ... }
```

## Further Reading

* [Clippy - error_impl_error](https://clippy.rust-lang.org/stable/index.html#error_impl_error)

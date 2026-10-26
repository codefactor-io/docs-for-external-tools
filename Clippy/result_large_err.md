Pattern: Large `Err` variant in `Result`

Issue: -

## Description

A `Result` is at least as large as the `Err`-variant. While we
expect that variant to be seldom used, the compiler needs to reserve
and move that much memory every single time.
Furthermore, errors are often simply passed up the call-stack, making
use of the `?`-operator and its type-conversion mechanics. If the
`Err`-variant further up the call-stack stores the `Err`-variant in
question (as library code often does), it itself needs to be at least
as large, propagating the problem.

## What it does

Checks for functions that return `Result` with an unusually large
`Err`-variant.

## Examples

Example of **incorrect** code:

```rust
pub enum ParseError {
    UnparsedBytes([u8; 512]),
    UnexpectedEof,
}

// The `Result` has at least 512 bytes, even in the `Ok`-case
pub fn parse() -> Result<(), ParseError> {
    Ok(())
}
```

Example of **correct** code:

```rust
pub enum ParseError {
    UnparsedBytes(Box<[u8; 512]>),
    UnexpectedEof,
}

// The `Result` is slightly larger than a pointer
pub fn parse() -> Result<(), ParseError> {
    Ok(())
}
```

## Known problems

The size determined by Clippy is platform-dependent.

## Further Reading

* [Clippy - result_large_err](https://clippy.rust-lang.org/stable/index.html#result_large_err)

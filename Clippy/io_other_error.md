Pattern: Missing use of `io::Error::other()`

Issue: -

## Description

Since Rust 1.74, there's the `io::Error::other(_)` shortcut.

## What it does

This lint warns on calling `io::Error::new(..)` with a kind of
`io::ErrorKind::Other`.

## Examples

Example of **incorrect** code:

```rust
use std::io;
let _ = io::Error::new(io::ErrorKind::Other, "bad".to_string());
```

Example of **correct** code:

```rust
let _ = std::io::Error::other("bad".to_string());
```

## Further Reading

* [Clippy - io_other_error](https://clippy.rust-lang.org/stable/index.html#io_other_error)

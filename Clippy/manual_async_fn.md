Pattern: Missing use of `async fn` syntax

Issue: -

## Description

It's more idiomatic to use the dedicated syntax.

## What it does

It checks for manual implementations of `async` functions.

## Examples

Example of **incorrect** code:

```rust
use std::future::Future;

fn foo() -> impl Future<Output = i32> { async { 42 } }
```

Example of **correct** code:

```rust
async fn foo() -> i32 { 42 }
```

## Further Reading

* [Clippy - manual_async_fn](https://clippy.rust-lang.org/stable/index.html#manual_async_fn)

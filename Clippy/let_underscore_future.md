Pattern: Future discarded with `let _`

Issue: -

## Description

Futures must be polled for work to be done. The original intention was most likely to await the future
and ignore the resulting value.

## What it does

Checks for `let _ = <expr>` where the resulting type of expr implements `Future`

## Examples

Example of **incorrect** code:

```rust
async fn foo() -> Result<(), ()> {
    Ok(())
}
let _ = foo();
```

Example of **correct** code:

```rust
async fn foo() -> Result<(), ()> {
    Ok(())
}
let _ = foo().await;
```

## Further Reading

* [Clippy - let_underscore_future](https://clippy.rust-lang.org/stable/index.html#let_underscore_future)

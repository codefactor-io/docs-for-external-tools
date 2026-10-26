Pattern: `async` block yielding unawaited future

Issue: -

## Description

An await is likely missing.

## What it does

Checks for async blocks that yield values of types
that can themselves be awaited.

## Examples

Example of **incorrect** code:

```rust
async fn foo() {}

fn bar() {
  let x = async {
    foo()
  };
}
```

Example of **correct** code:

```rust
async fn foo() {}

fn bar() {
  let x = async {
    foo().await
  };
}
```

## Further Reading

* [Clippy - async_yields_async](https://clippy.rust-lang.org/stable/index.html#async_yields_async)

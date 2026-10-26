Pattern: Large future

Issue: -

## Description

Due to the current [unideal implementation](https://github.com/rust-lang/rust/issues/69826) of `Coroutine`,
large size of a `Future` may cause stack overflows.

## What it does

It checks for the size of a `Future` created by `async fn` or `async {}`.

## Examples

```rust
async fn large_future(_x: [u8; 16 * 1024]) {}

pub async fn trigger() {
    large_future([0u8; 16 * 1024]).await;
}
```

`Box::pin` the big future instead.

```rust
async fn large_future(_x: [u8; 16 * 1024]) {}

pub async fn trigger() {
    Box::pin(large_future([0u8; 16 * 1024])).await;
}
```

## Further Reading

* [Clippy - large_futures](https://clippy.rust-lang.org/stable/index.html#large_futures)

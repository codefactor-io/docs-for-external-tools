Pattern: `async` function without `await`

Issue: -

## Description

Async functions with no async code create overhead, both mentally and computationally.
Callers of async methods either need to be calling from an async function themselves or run it on an executor, both of which
causes runtime overhead and hassle for the caller.

## What it does

Checks for functions that are declared `async` but have no `.await`s inside of them.

## Examples

Example of **incorrect** code:

```rust
async fn get_random_number() -> i64 {
    4 // Chosen by fair dice roll. Guaranteed to be random.
}
let number_future = get_random_number();
```

Example of **correct** code:

```rust
fn get_random_number_improved() -> i64 {
    4 // Chosen by fair dice roll. Guaranteed to be random.
}
let number_future = async { get_random_number_improved() };
```

## Further Reading

* [Clippy - unused_async](https://clippy.rust-lang.org/stable/index.html#unused_async)

Pattern: `async` trait method without `await`

Issue: -

## Description

Async functions with no async code create computational overhead.
Even though the trait requires the method to return a future,
returning a `core::future::ready` with the result is more efficient
as it reduces the number of states in the Future state machine by at least one.

Note that the behaviour is slightly different when using `core::future::ready`,
as the value is computed immediately and stored in a future for later retrieval at the first (and only valid) call to `poll`.
An `async` block generates code that completely defers the computation of this value until the Future is polled.

## What it does

Checks for trait method implementations that are declared `async` but have no `.await`s inside of them.

## Examples

Example of **incorrect** code:

```rust
trait AsyncTrait {
    async fn get_random_number() -> i64;
}

impl AsyncTrait for () {
    async fn get_random_number() -> i64 {
        4 // Chosen by fair dice roll. Guaranteed to be random.
    }
}
```

Example of **correct** code:

```rust
trait AsyncTrait {
    async fn get_random_number() -> i64;
}

impl AsyncTrait for () {
    fn get_random_number() -> impl Future<Output = i64> {
        core::future::ready(4) // Chosen by fair dice roll. Guaranteed to be random.
    }
}
```

## Further Reading

* [Clippy - unused_async_trait_impl](https://clippy.rust-lang.org/stable/index.html#unused_async_trait_impl)

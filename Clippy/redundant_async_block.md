Pattern: Redundant `async` block

Issue: -

## Description

It is simpler and more efficient to use the future directly.

## What it does

Checks for `async` block that only returns `await` on a future.

## Examples

Example of **incorrect** code:

```rust
let f = async {
    1 + 2
};
let fut = async {
    f.await
};
```

Example of **correct** code:

```rust
let f = async {
    1 + 2
};
let fut = f;
```

## Further Reading

* [Clippy - redundant_async_block](https://clippy.rust-lang.org/stable/index.html#redundant_async_block)

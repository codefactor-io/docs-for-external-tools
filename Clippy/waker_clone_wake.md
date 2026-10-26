Pattern: Unnecessary `Waker` clone before `wake()`

Issue: -

## Description

Cloning the waker is not necessary, `wake_by_ref()` enables the same operation
without extra cloning/dropping.

## What it does

Checks for usage of `waker.clone().wake()`

## Examples

Example of **incorrect** code:

```rust
waker.clone().wake();
```

Example of **correct** code:

```rust
waker.wake_by_ref();
```

## Further Reading

* [Clippy - waker_clone_wake](https://clippy.rust-lang.org/stable/index.html#waker_clone_wake)

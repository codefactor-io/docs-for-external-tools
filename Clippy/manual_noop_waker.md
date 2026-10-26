Pattern: Missing use of `Waker::noop()`

Issue: -

## Description

`Waker::noop()` provides a more performant and cleaner way to create a
waker that does nothing, avoiding unnecessary `Arc` allocations and
reference count increments.

## What it does

Checks for manual implementations of `std::task::Wake` that are empty.

## Examples

Example of **incorrect** code:

```rust
struct MyWaker;
impl Wake for MyWaker {
    fn wake(self: Arc<Self>) {}
    fn wake_by_ref(self: &Arc<Self>) {}
}
```

Example of **correct** code:

```rust
use std::task::Waker;
let waker = Waker::noop();
```

## Further Reading

* [Clippy - manual_noop_waker](https://clippy.rust-lang.org/stable/index.html#manual_noop_waker)

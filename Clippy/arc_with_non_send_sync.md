Pattern: `Arc` with non-`Send` or non-`Sync` type

Issue: -

## Description

`Arc<T>` is a thread-safe `Rc<T>` and guarantees that updates to the reference counter
use atomic operations. To send an `Arc<T>` across thread boundaries and
share ownership between multiple threads, `T` must be [both `Send` and `Sync`](https://doc.rust-lang.org/std/sync/struct.Arc.html#thread-safety),
so either `T` should be made `Send + Sync` or an `Rc` should be used instead of an `Arc`.

## What it does

This lint warns when you use `Arc` with a type that does not implement `Send` or `Sync`.

## Examples

```rust

fn main() {
    // This is fine, as `i32` implements `Send` and `Sync`.
    let a = Arc::new(42);

    // `RefCell` is `!Sync`, so either the `Arc` should be replaced with an `Rc`
    // or the `RefCell` replaced with something like a `RwLock`
    let b = Arc::new(RefCell::new(42));
}
```

## Further Reading

* [Clippy - arc_with_non_send_sync](https://clippy.rust-lang.org/stable/index.html#arc_with_non_send_sync)

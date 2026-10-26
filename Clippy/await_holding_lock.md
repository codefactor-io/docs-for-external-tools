Pattern: `MutexGuard` held across `await`

Issue: -

## Description

The Mutex types found in [`std::sync`](https://doc.rust-lang.org/stable/std/sync/) and
[`parking_lot`](https://docs.rs/parking_lot/latest/parking_lot/) are
not designed to operate in an async context across await points.

There are two potential solutions. One is to use an async-aware `Mutex`
type. Many asynchronous foundation crates provide such a `Mutex` type.
The other solution is to ensure the mutex is unlocked before calling
`await`, either by introducing a scope or an explicit call to
[`Drop::drop`](https://doc.rust-lang.org/std/ops/trait.Drop.html).

## What it does

Checks for calls to `await` while holding a non-async-aware
`MutexGuard`.

## Examples

Example of **incorrect** code:

```rust
async fn foo(x: &Mutex<u32>) {
  let mut guard = x.lock().unwrap();
  *guard += 1;
  baz().await;
}

async fn bar(x: &Mutex<u32>) {
  let mut guard = x.lock().unwrap();
  *guard += 1;
  drop(guard); // explicit drop
  baz().await;
}
```

Example of **correct** code:

```rust
async fn foo(x: &Mutex<u32>) {
  {
    let mut guard = x.lock().unwrap();
    *guard += 1;
  }
  baz().await;
}

async fn bar(x: &Mutex<u32>) {
  {
    let mut guard = x.lock().unwrap();
    *guard += 1;
  } // guard dropped here at end of scope
  baz().await;
}
```

## Known problems

Will report false positive for explicitly dropped guards
([#6446](https://github.com/rust-lang/rust-clippy/issues/6446)). A
workaround for this is to wrap the `.lock()` call in a block instead of
explicitly dropping the guard.

## Further Reading

* [Clippy - await_holding_lock](https://clippy.rust-lang.org/stable/index.html#await_holding_lock)

Pattern: Write lock used only for reading

Issue: -

## Description

The write portion of `RwLock` is exclusive, meaning that no other thread
can access the lock while this writer is active.

## What it does

Looks for calls to `RwLock::write` where the lock is only used for reading.

## Examples

Example of **incorrect** code:

```rust
use std::sync::RwLock;
fn assert_is_zero(lock: &RwLock<i32>) {
    let num = lock.write().unwrap();
    assert_eq!(*num, 0);
}
```

Example of **correct** code:

```rust
use std::sync::RwLock;
fn assert_is_zero(lock: &RwLock<i32>) {
    let num = lock.read().unwrap();
    assert_eq!(*num, 0);
}
```

## Further Reading

* [Clippy - readonly_write_lock](https://clippy.rust-lang.org/stable/index.html#readonly_write_lock)

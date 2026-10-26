Pattern: Lock discarded with `let _`

Issue: -

## Description

This statement immediately drops the lock instead of
extending its lifetime to the end of the scope, which is often not intended.
To extend lock lifetime to the end of the scope, use an underscore-prefixed
name instead (i.e. _lock). If you want to explicitly drop the lock,
`std::mem::drop` conveys your intention better and is less error-prone.

## What it does

Checks for `let _ = sync_lock`. This supports `mutex` and `rwlock` in
`parking_lot`. For `std` locks see the `rustc` lint
[`let_underscore_lock`](https://doc.rust-lang.org/nightly/rustc/lints/listing/deny-by-default.html#let-underscore-lock)

## Examples

Example of **incorrect** code:

```rust
let _ = mutex.lock();
```

Example of **correct** code:

```rust
let _lock = mutex.lock();
```

## Further Reading

* [Clippy - let_underscore_lock](https://clippy.rust-lang.org/stable/index.html#let_underscore_lock)

Pattern: Use of `Mutex` for integer

Issue: -

## Description

Using a mutex just to make access to a plain integer
sequential is
shooting flies with cannons. `std::sync::atomic::AtomicUsize` is leaner and faster.

On the other hand, `Mutex`es are, in general, easier to
verify correctness. An atomic does not behave the same as
an equivalent mutex. See [this issue](https://github.com/rust-lang/rust-clippy/issues/4295)'s
commentary for more details.

## What it does

Checks for usage of `Mutex<X>` where `X` is an integral
type.

## Examples

Example of **incorrect** code:

```rust
let x = Mutex::new(0usize);
```

Example of **correct** code:

```rust
let x = AtomicUsize::new(0usize);
```

## Known problems

* This lint cannot detect if the mutex is actually used
  for waiting before a critical section.
* This lint has a false positive that warns without considering the case
  where `Mutex` is used together with `Condvar`.
* This lint suggest using `AtomicU64` instead of `Mutex<u64>`, but
  `AtomicU64` is not available on some 32-bit platforms.

## Further Reading

* [Clippy - mutex_integer](https://clippy.rust-lang.org/stable/index.html#mutex_integer)

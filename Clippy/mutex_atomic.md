Pattern: Use of `Mutex` instead of atomic type

Issue: -

## Description

Using a mutex just to make access to a plain bool or
reference sequential is shooting flies with cannons.
`std::sync::atomic::AtomicBool` and `std::sync::atomic::AtomicPtr` are leaner and
faster.

On the other hand, `Mutex`es are, in general, easier to
verify correctness. An atomic does not behave the same as
an equivalent mutex. See [this issue](https://github.com/rust-lang/rust-clippy/issues/4295)'s
commentary for more details.

## What it does

Checks for usage of `Mutex<X>` where an atomic will do.

## Examples

Example of **incorrect** code:

```rust
let x = Mutex::new(&y);
```

Example of **correct** code:

```rust
let x = AtomicBool::new(y);
```

## Known problems

* This lint cannot detect if the mutex is actually used
  for waiting before a critical section.
* This lint has a false positive that warns without considering the case
  where `Mutex` is used together with `Condvar`.

## Further Reading

* [Clippy - mutex_atomic](https://clippy.rust-lang.org/stable/index.html#mutex_atomic)

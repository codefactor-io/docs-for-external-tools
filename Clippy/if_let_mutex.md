Pattern: `Mutex` locked again in `else` of `if let`

Issue: -

## Description

The Mutex lock remains held for the whole
`if let ... else` block and deadlocks.

## What it does

Checks for `Mutex::lock` calls in `if let` expression
with lock calls in any of the else blocks.

## Examples

Example of **incorrect** code:

```rust
if let Ok(thing) = mutex.lock() {
    do_thing();
} else {
    mutex.lock();
}
```

Example of **correct** code:

```rust
let locked = mutex.lock();
if let Ok(thing) = locked {
    do_thing(thing);
} else {
    use_locked(locked);
}
```

## Disabled starting in Edition 2024

This lint is effectively disabled starting in
Edition 2024 as `if let ... else` scoping was reworked
such that this is no longer an issue. See
[Proposal: stabilize if_let_rescope for Edition 2024](https://github.com/rust-lang/rust/issues/131154)

## Further Reading

* [Clippy - if_let_mutex](https://clippy.rust-lang.org/stable/index.html#if_let_mutex)

Pattern: Missing use of `mem::swap()`

Issue: -

## Description

The `std::mem::swap` function exposes the intent better
without deinitializing or copying either variable.

## What it does

Checks for manual swapping.

Note that the lint will not be emitted in const blocks, as the suggestion would not be applicable.

## Examples

```rust
let mut a = 42;
let mut b = 1337;

let t = b;
b = a;
a = t;
```
Use std::mem::swap():
```rust
let mut a = 1;
let mut b = 2;
std::mem::swap(&mut a, &mut b);
```

## Further Reading

* [Clippy - manual_swap](https://clippy.rust-lang.org/stable/index.html#manual_swap)

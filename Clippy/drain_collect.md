Pattern: Use of `drain(..).collect()`

Issue: -

## Description

Using `mem::take` is faster as it avoids the allocation.
When using `mem::take`, the old collection is replaced with an empty one and ownership of
the old collection is returned.

## What it does

Checks for calls to `.drain()` that clear the collection, immediately followed by a call to `.collect()`.

> "Collection" in this context refers to any type with a `drain` method:
> `Vec`, `VecDeque`, `BinaryHeap`, `HashSet`,`HashMap`, `String`

## Examples

Example of **incorrect** code:

```rust
fn remove_all(v: &mut Vec<i32>) -> Vec<i32> {
    v.drain(..).collect()
}
```

Example of **correct** code:

```rust
use std::mem;
fn remove_all(v: &mut Vec<i32>) -> Vec<i32> {
    mem::take(v)
}
```

## Known issues

`mem::take(&mut vec)` is almost equivalent to `vec.drain(..).collect()`, except that
it also moves the **capacity**. The user might have explicitly written it this way
to keep the capacity on the original `Vec`.

## Further Reading

* [Clippy - drain_collect](https://clippy.rust-lang.org/stable/index.html#drain_collect)

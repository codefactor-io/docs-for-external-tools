Pattern: Use of `MaybeUninit::uninit().assume_init()`

Issue: -

## Description

For most types, this is undefined behavior.

## What it does

Checks for `MaybeUninit::uninit().assume_init()`.

## Examples

```rust
// Beware the UB
use std::mem::MaybeUninit;

let _: usize = unsafe { MaybeUninit::uninit().assume_init() };
```

Note that the following is OK:

```rust
use std::mem::MaybeUninit;

let _: [MaybeUninit<bool>; 5] = unsafe {
    MaybeUninit::uninit().assume_init()
};
```

## Known problems

For now, we accept empty tuples and tuples / arrays
of `MaybeUninit`. There may be other types that allow uninitialized
data, but those are not yet rigorously defined.

## Further Reading

* [Clippy - uninit_assumed_init](https://clippy.rust-lang.org/stable/index.html#uninit_assumed_init)

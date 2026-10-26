Pattern: Missing use of `BuildHasher::hash_one()`

Issue: -

## Description

It is more concise to use the `hash_one` method.

## What it does

Checks for cases where [`BuildHasher::hash_one`] can be used.

[`BuildHasher::hash_one`]: https://doc.rust-lang.org/std/hash/trait.BuildHasher.html#method.hash_one

## Examples

Example of **incorrect** code:

```rust
use std::hash::{BuildHasher, Hash, Hasher};
use std::collections::hash_map::RandomState;

let s = RandomState::new();
let value = vec![1, 2, 3];

let mut hasher = s.build_hasher();
value.hash(&mut hasher);
let hash = hasher.finish();
```

Example of **correct** code:

```rust
use std::hash::BuildHasher;
use std::collections::hash_map::RandomState;

let s = RandomState::new();
let value = vec![1, 2, 3];

let hash = s.hash_one(&value);
```

## Further Reading

* [Clippy - manual_hash_one](https://clippy.rust-lang.org/stable/index.html#manual_hash_one)

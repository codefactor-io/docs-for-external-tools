Pattern: Mutable key type in map or set

Issue: -

## Description

All of `HashMap`, `HashSet`, `BTreeMap` and
`BtreeSet` rely on either the hash or the order of keys be unchanging,
so having types with interior mutability is a bad idea.

## What it does

Checks for sets/maps with mutable key types.

## Examples

Example of **incorrect** code:

```rust
use std::cmp::{PartialEq, Eq};
use std::collections::HashSet;
use std::hash::{Hash, Hasher};
use std::sync::atomic::AtomicUsize;

struct Bad(AtomicUsize);
impl PartialEq for Bad {
    fn eq(&self, rhs: &Self) -> bool {
         ..
    }
}

impl Eq for Bad {}

impl Hash for Bad {
    fn hash<H: Hasher>(&self, h: &mut H) {
        ..
    }
}

fn main() {
    let _: HashSet<Bad> = HashSet::new();
}
```

## Known problems

#### False Positives
It's correct to use a struct that contains interior mutability as a key when its
implementation of `Hash` or `Ord` doesn't access any of the interior mutable types.
However, this lint is unable to recognize this, so it will often cause false positives in
these cases.

#### False Negatives
This lint does not follow raw pointers (`*const T` or `*mut T`) as `Hash` and `Ord`
apply only to the **address** of the contained value. This can cause false negatives for
custom collections that use raw pointers internally.

## Further Reading

* [Clippy - mutable_key_type](https://clippy.rust-lang.org/stable/index.html#mutable_key_type)

Pattern: `Hash` with `Borrow<str>` and `Borrow<[u8]>`

Issue: -

## Description

When providing implementations for `Borrow<T>`, one should consider whether the different
implementations should act as facets or representations of the underlying type. Generic code
typically uses `Borrow<T>` when it relies on the identical behavior of these additional trait
implementations. These traits will likely appear as additional trait bounds.

In particular `Eq`, `Ord` and `Hash` must be equivalent for borrowed and owned values:
`x.borrow() == y.borrow()` should give the same result as `x == y`.
It follows then that the following equivalence must hold:
`hash(x) == hash((x as Borrow<[u8]>).borrow()) == hash((x as Borrow<str>).borrow())`

Unfortunately it doesn't hold as `hash("abc") != hash("abc".as_bytes())`.
This happens because the `Hash` impl for str passes an additional `0xFF` byte to
the hasher to avoid collisions. For example, given the tuples `("a", "bc")`, and `("ab", "c")`,
the two tuples would have the same hash value if the `0xFF` byte was not added.

## What it does

This lint is concerned with the semantics of `Borrow` and `Hash` for a
type that implements all three of `Hash`, `Borrow<str>` and `Borrow<[u8]>`
as it is impossible to satisfy the semantics of Borrow and `Hash` for
both `Borrow<str>` and `Borrow<[u8]>`.

## Examples

```rust
use std::borrow::Borrow;
use std::hash::{Hash, Hasher};

struct ExampleType {
    data: String
}

impl Hash for ExampleType {
    fn hash<H: Hasher>(&self, state: &mut H) {
        self.data.hash(state);
    }
}

impl Borrow<str> for ExampleType {
    fn borrow(&self) -> &str {
        &self.data
    }
}

impl Borrow<[u8]> for ExampleType {
    fn borrow(&self) -> &[u8] {
        self.data.as_bytes()
    }
}
```
As a consequence, hashing a `&ExampleType` and hashing the result of the two
borrows will result in different values.

## Further Reading

* [Clippy - impl_hash_borrow_with_str_and_bytes](https://clippy.rust-lang.org/stable/index.html#impl_hash_borrow_with_str_and_bytes)

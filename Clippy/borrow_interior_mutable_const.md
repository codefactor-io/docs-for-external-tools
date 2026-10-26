Pattern: Borrow of `const` with interior mutability

Issue: -

## Description

Named constants are copied at every use site which means any change to their value
will be lost after the newly created value is dropped. e.g.

```rust
use core::sync::atomic::{AtomicUsize, Ordering};
const ATOMIC: AtomicUsize = AtomicUsize::new(0);
fn add_one() -> usize {
    // This will always return `0` since `ATOMIC` is copied before it's borrowed
    // for use by `fetch_add`.
    ATOMIC.fetch_add(1, Ordering::AcqRel)
}
```

## What it does

Checks for a borrow of a named constant with interior mutability.

## Examples

Example of **incorrect** code:

```rust
use std::sync::atomic::{AtomicUsize, Ordering::SeqCst};
const CONST_ATOM: AtomicUsize = AtomicUsize::new(12);

CONST_ATOM.store(6, SeqCst); // the content of the atomic is unchanged
assert_eq!(CONST_ATOM.load(SeqCst), 12); // because the CONST_ATOM in these lines are distinct
```

Example of **correct** code:

```rust
use std::sync::atomic::{AtomicUsize, Ordering::SeqCst};
const CONST_ATOM: AtomicUsize = AtomicUsize::new(12);

static STATIC_ATOM: AtomicUsize = CONST_ATOM;
STATIC_ATOM.store(9, SeqCst);
assert_eq!(STATIC_ATOM.load(SeqCst), 9); // use a `static` item to refer to the same instance
```

## Known problems

This lint does not, and cannot in general, determine if the borrow of the constant
is used in a way which causes a mutation. e.g.

```rust
use core::cell::Cell;
const CELL: Cell<usize> = Cell::new(0);
fn get_cell() -> Cell<usize> {
    // This is fine. It borrows a copy of `CELL`, but never mutates it through the
    // borrow.
    CELL.clone()
}
```

There also exists types which contain private fields with interior mutability, but
no way to both create a value as a constant and modify any mutable field using the
type's public interface (e.g. `bytes::Bytes`). As there is no reasonable way to
scan a crate's interface to see if this is the case, all such types will be linted.
If this happens use the `ignore-interior-mutability` configuration option to allow
the type.

## Further Reading

* [Clippy - borrow_interior_mutable_const](https://clippy.rust-lang.org/stable/index.html#borrow_interior_mutable_const)

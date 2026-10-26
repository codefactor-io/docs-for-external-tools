Pattern: `const` with interior mutability

Issue: -

## Description

Named constants are copied at every use site which means any change to their value
will be lost after the newly created value is dropped. e.g.

```rust
use core::sync::atomic::{AtomicUsize, Ordering};
const ATOMIC: AtomicUsize = AtomicUsize::new(0);
fn add_one() -> usize {
    // This will always return `0` since `ATOMIC` is copied before it's used.
    ATOMIC.fetch_add(1, Ordering::AcqRel)
}
```

If shared modification of the value is desired, a `static` item is needed instead.
If that is not desired, a `const fn` constructor should be used to make it obvious
at the use site that a new value is created.

## What it does

Checks for the declaration of named constant which contain interior mutability.

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
static STATIC_ATOM: AtomicUsize = AtomicUsize::new(15);
STATIC_ATOM.store(9, SeqCst);
assert_eq!(STATIC_ATOM.load(SeqCst), 9); // use a `static` item to refer to the same instance
```

## Known problems

Prior to `const fn` stabilization this was the only way to provide a value which
could initialize a `static` item (e.g. the `std::sync::ONCE_INIT` constant). In
this case the use of `const` is required and this lint should be suppressed.

There also exists types which contain private fields with interior mutability, but
no way to both create a value as a constant and modify any mutable field using the
type's public interface (e.g. `bytes::Bytes`). As there is no reasonable way to
scan a crate's interface to see if this is the case, all such types will be linted.
If this happens use the `ignore-interior-mutability` configuration option to allow
the type.

## Further Reading

* [Clippy - declare_interior_mutable_const](https://clippy.rust-lang.org/stable/index.html#declare_interior_mutable_const)

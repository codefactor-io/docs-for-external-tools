Pattern: Import from `alloc` instead of `core`

Issue: -

## Description

Crates which have `no_std` compatibility and may optionally require alloc may wish to ensure types are
imported from core to ensure disabling `alloc` does not cause the crate to fail to compile. This lint
is also useful for crates migrating to become `no_std` compatible.

## What it does

Finds items imported through `alloc` when available through `core`.

## Examples

Example of **incorrect** code:

```rust
use alloc::slice::from_ref;
```

Example of **correct** code:

```rust
use core::slice::from_ref;
```

## Known problems

The lint is only partially aware of the required MSRV for items that were originally in `std` but moved
to `core`.

## Further Reading

* [Clippy - alloc_instead_of_core](https://clippy.rust-lang.org/stable/index.html#alloc_instead_of_core)

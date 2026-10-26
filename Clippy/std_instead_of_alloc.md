Pattern: Import from `std` instead of `alloc`

Issue: -

## Description

Crates which have `no_std` compatibility and require alloc may wish to ensure types are imported from
alloc to ensure disabling `std` does not cause the crate to fail to compile. This lint is also useful
for crates migrating to become `no_std` compatible.

## What it does

Finds items imported through `std` when available through `alloc`.

## Examples

Example of **incorrect** code:

```rust
use std::vec::Vec;
```

Example of **correct** code:

```rust
use alloc::vec::Vec;
```

## Further Reading

* [Clippy - std_instead_of_alloc](https://clippy.rust-lang.org/stable/index.html#std_instead_of_alloc)

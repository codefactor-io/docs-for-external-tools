Pattern: Import from `std` instead of `core`

Issue: -

## Description

Crates which have `no_std` compatibility may wish to ensure types are imported from core to ensure
disabling `std` does not cause the crate to fail to compile. This lint is also useful for crates
migrating to become `no_std` compatible.

## What it does

Finds items imported through `std` when available through `core`.

## Examples

Example of **incorrect** code:

```rust
use std::hash::Hasher;
```

Example of **correct** code:

```rust
use core::hash::Hasher;
```

## Further Reading

* [Clippy - std_instead_of_core](https://clippy.rust-lang.org/stable/index.html#std_instead_of_core)

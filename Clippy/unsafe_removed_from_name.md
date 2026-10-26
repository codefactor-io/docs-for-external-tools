Pattern: `unsafe` removed from name on import

Issue: -

## Description

Renaming makes it less clear which traits and
structures are unsafe.

## What it does

Checks for imports that remove "unsafe" from an item's
name.

## Examples

Example of **incorrect** code:

```rust
use std::cell::{UnsafeCell as TotallySafeCell};

extern crate crossbeam;
use crossbeam::{spawn_unsafe as spawn};
```

## Further Reading

* [Clippy - unsafe_removed_from_name](https://clippy.rust-lang.org/stable/index.html#unsafe_removed_from_name)

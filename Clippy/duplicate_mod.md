Pattern: File loaded as module multiple times

Issue: -

## Description

Loading a file as a module more than once causes it to be compiled
multiple times, taking longer and putting duplicate content into the
module tree.

## What it does

Checks for files that are included as modules multiple times.

## Examples

```rust
// lib.rs
mod a;
mod b;
```
```rust
// a.rs
#[path = "./b.rs"]
mod b;
```

Use instead:

```rust
// lib.rs
mod a;
mod b;
```
```rust
// a.rs
use crate::b;
```

## Further Reading

* [Clippy - duplicate_mod](https://clippy.rust-lang.org/stable/index.html#duplicate_mod)

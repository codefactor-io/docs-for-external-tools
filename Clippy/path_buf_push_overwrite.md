Pattern: Use of `PathBuf::push()` with absolute path

Issue: -

## Description

Calling `push` with a root path at the start can overwrite the
previous defined path.

## What it does

* Checks for [push](https://doc.rust-lang.org/std/path/struct.PathBuf.html#method.push)
calls on `PathBuf` that can cause overwrites.

## Examples

Example of **incorrect** code:

```rust
use std::path::PathBuf;

let mut x = PathBuf::from("/foo");
x.push("/bar");
assert_eq!(x, PathBuf::from("/bar"));
```

Example of **correct** code:

```rust
use std::path::PathBuf;

let mut x = PathBuf::from("/foo");
x.push("bar");
assert_eq!(x, PathBuf::from("/foo/bar"));
```

## Further Reading

* [Clippy - path_buf_push_overwrite](https://clippy.rust-lang.org/stable/index.html#path_buf_push_overwrite)

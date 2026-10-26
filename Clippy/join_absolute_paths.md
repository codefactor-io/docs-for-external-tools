Pattern: `Path::join()` with absolute path

Issue: -

## Description

If the argument to `Path::join` starts with a separator, it will overwrite
the original path. If this is intentional, prefer using `Path::new` instead.

Note the behavior is platform dependent. A leading `\\` will be accepted
on unix systems as part of the file name

See [`Path::join`](https://doc.rust-lang.org/std/path/struct.Path.html#method.join)

## What it does

Checks for calls to `Path::join` that start with a path separator (`\\` or `/`).

## Examples

Example of **incorrect** code:

```rust
let path = Path::new("/bin");
let joined_path = path.join("/sh");
assert_eq!(joined_path, PathBuf::from("/sh"));
```

Example of **correct** code:

```rust
let path = Path::new("/bin");

// If this was unintentional, remove the leading separator
let joined_path = path.join("sh");
assert_eq!(joined_path, PathBuf::from("/bin/sh"));

// If this was intentional, create a new path instead
let new = Path::new("/sh");
assert_eq!(new, PathBuf::from("/sh"));
```

## Further Reading

* [Clippy - join_absolute_paths](https://clippy.rust-lang.org/stable/index.html#join_absolute_paths)

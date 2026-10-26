Pattern: Use of `set_readonly(false)` on permissions

Issue: -

## Description

On Unix platforms this results in the file being world writable,
equivalent to `chmod a+w <file>`.

## What it does

Checks for calls to `std::fs::Permissions.set_readonly` with argument `false`.

## Examples

Example of **incorrect** code:

```rust
use std::fs::File;
let f = File::create("foo.txt").unwrap();
let metadata = f.metadata().unwrap();
let mut permissions = metadata.permissions();
permissions.set_readonly(false);
```

## Further Reading

* [Clippy - permissions_set_readonly_false](https://clippy.rust-lang.org/stable/index.html#permissions_set_readonly_false)

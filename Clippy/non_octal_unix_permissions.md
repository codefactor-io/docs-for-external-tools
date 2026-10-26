Pattern: Non-octal Unix permissions value

Issue: -

## Description

They will be converted into octal, creating potentially
unintended file permissions.

## What it does

Checks for non-octal values used to set Unix file permissions.

## Examples

Example of **incorrect** code:

```rust
use std::fs::OpenOptions;
use std::os::unix::fs::OpenOptionsExt;

let mut options = OpenOptions::new();
options.mode(644);
```

Example of **correct** code:

```rust
use std::fs::OpenOptions;
use std::os::unix::fs::OpenOptionsExt;

let mut options = OpenOptions::new();
options.mode(0o644);
```

## Further Reading

* [Clippy - non_octal_unix_permissions](https://clippy.rust-lang.org/stable/index.html#non_octal_unix_permissions)

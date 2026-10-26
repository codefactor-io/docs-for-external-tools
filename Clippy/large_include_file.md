Pattern: Large included file

Issue: -

## Description

Including large files can undesirably increase the size of the binary produced by the compiler.
This lint may be used to catch mistakes where an unexpectedly large file is included, or
temporarily to obtain a list of all large files.

## What it does

Checks for the inclusion of large files via `include_bytes!()`
or `include_str!()`.

## Examples

Example of **incorrect** code:

```rust
let included_str = include_str!("very_large_file.txt");
let included_bytes = include_bytes!("very_large_file.txt");
```

Example of **correct** code:

```rust
use std::fs;

// You can load the file at runtime
let string = fs::read_to_string("very_large_file.txt")?;
let bytes = fs::read("very_large_file.txt")?;
```

## Further Reading

* [Clippy - large_include_file](https://clippy.rust-lang.org/stable/index.html#large_include_file)

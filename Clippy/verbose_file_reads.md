Pattern: Verbose file read

Issue: -

## Description

`fs::{read, read_to_string}` provide the same functionality when `buf` is empty with fewer imports and no intermediate values.
See also: [fs::read docs](https://doc.rust-lang.org/std/fs/fn.read.html), [fs::read_to_string docs](https://doc.rust-lang.org/std/fs/fn.read_to_string.html)

## What it does

Checks for usage of File::read_to_end and File::read_to_string.

## Examples

```rust
let mut f = File::open("foo.txt").unwrap();
let mut bytes = Vec::new();
f.read_to_end(&mut bytes).unwrap();
```
Can be written more concisely as
```rust
let mut bytes = fs::read("foo.txt").unwrap();
```

## Further Reading

* [Clippy - verbose_file_reads](https://clippy.rust-lang.org/stable/index.html#verbose_file_reads)

Pattern: `Read::bytes()` on unbuffered reader

Issue: -

## Description

The default implementation calls `read` for each byte, which can be very inefficient for data that's not in memory, such as `File`.

## What it does

Checks for calls to `Read::bytes` on types which don't implement `BufRead`.

## Examples

Example of **incorrect** code:

```rust
use std::io::Read;
use std::fs::File;
let file = File::open("./bytes.txt").unwrap();
file.bytes();
```

Example of **correct** code:

```rust
use std::io::{BufReader, Read};
use std::fs::File;
let file = BufReader::new(File::open("./bytes.txt").unwrap());
file.bytes();
```

## Further Reading

* [Clippy - unbuffered_bytes](https://clippy.rust-lang.org/stable/index.html#unbuffered_bytes)

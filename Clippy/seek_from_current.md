Pattern: Missing use of `stream_position()`

Issue: -

## Description

Readability. Use dedicated method.

## What it does

Checks if the `seek` method of the `Seek` trait is called with `SeekFrom::Current(0)`,
and if it is, suggests using `stream_position` instead.

## Examples

Example of **incorrect** code:

```rust
use std::fs::File;
use std::io::{self, Write, Seek, SeekFrom};

fn main() -> io::Result<()> {
    let mut f = File::create("foo.txt")?;
    f.write_all(b"Hello")?;
    eprintln!("Written {} bytes", f.seek(SeekFrom::Current(0))?);

    Ok(())
}
```

Example of **correct** code:

```rust
use std::fs::File;
use std::io::{self, Write, Seek, SeekFrom};

fn main() -> io::Result<()> {
    let mut f = File::create("foo.txt")?;
    f.write_all(b"Hello")?;
    eprintln!("Written {} bytes", f.stream_position()?);

    Ok(())
}
```

## Further Reading

* [Clippy - seek_from_current](https://clippy.rust-lang.org/stable/index.html#seek_from_current)

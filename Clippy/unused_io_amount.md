Pattern: Unused read or write byte count

Issue: -

## Description

`io::Write::write(_vectored)` and
`io::Read::read(_vectored)` are not guaranteed to
process the entire buffer. They return how many bytes were processed, which
might be smaller
than a given buffer's length. If you don't need to deal with
partial-write/read, use
`write_all`/`read_exact` instead.

When working with asynchronous code (either with the `futures`
crate or with `tokio`), a similar issue exists for
`AsyncWriteExt::write()` and `AsyncReadExt::read()` : these
functions are also not guaranteed to process the entire
buffer.  Your code should either handle partial-writes/reads, or
call the `write_all`/`read_exact` methods on those traits instead.

## What it does

Checks for unused written/read amount.

## Examples

Example of **incorrect** code:

```rust
use std::io;
fn foo<W: io::Write>(w: &mut W) -> io::Result<()> {
    w.write(b"foo")?;
    Ok(())
}
```

Example of **correct** code:

```rust
use std::io;
fn foo<W: io::Write>(w: &mut W) -> io::Result<()> {
    w.write_all(b"foo")?;
    Ok(())
}
```

## Known problems

Detects only common patterns.

## Further Reading

* [Clippy - unused_io_amount](https://clippy.rust-lang.org/stable/index.html#unused_io_amount)

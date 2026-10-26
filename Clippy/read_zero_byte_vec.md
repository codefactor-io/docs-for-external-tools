Pattern: Read into zero-length `Vec`

Issue: -

## Description

Reading zero bytes is almost certainly not the intended behavior.

## What it does

This lint catches reads into a zero-length `Vec`.
Especially in the case of a call to `with_capacity`, this lint warns that read
gets the number of bytes from the `Vec`'s length, not its capacity.

## Examples

Example of **incorrect** code:

```rust
use std::io;
fn foo<F: io::Read>(mut f: F) {
    let mut data = Vec::with_capacity(100);
    f.read(&mut data).unwrap();
}
```

Example of **correct** code:

```rust
use std::io;
fn foo<F: io::Read>(mut f: F) {
    let mut data = Vec::with_capacity(100);
    data.resize(100, 0);
    f.read(&mut data).unwrap();
}
```

## Known problems

In theory, a very unusual read implementation could assign some semantic meaning
to zero-byte reads. But it seems exceptionally unlikely that code intending to do
a zero-byte read would allocate a `Vec` for it.

## Further Reading

* [Clippy - read_zero_byte_vec](https://clippy.rust-lang.org/stable/index.html#read_zero_byte_vec)

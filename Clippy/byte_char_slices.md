Pattern: Slice of byte chars instead of byte string

Issue: -

## Description

Potentially makes the string harder to read.

## What it does

Checks for hard to read slices of byte characters, that could be more easily expressed as a
byte string.

## Examples

Example of **incorrect** code:

```rust
&[b'H', b'e', b'l', b'l', b'o'];
```

Example of **correct** code:

```rust
b"Hello"
```

## Further Reading

* [Clippy - byte_char_slices](https://clippy.rust-lang.org/stable/index.html#byte_char_slices)

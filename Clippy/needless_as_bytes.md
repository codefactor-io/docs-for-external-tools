Pattern: Unnecessary `as_bytes()` call

Issue: -

## Description

The `len()` and `is_empty()` methods are also directly available on strings, and they
return identical results. In particular, `len()` on a string returns the number of
bytes.

## What it does

It detects useless calls to `str::as_bytes()` before calling `len()` or `is_empty()`.

## Examples

Example of **incorrect** code:

```rust
let len = "some string".as_bytes().len();
let b = "some string".as_bytes().is_empty();
```

Example of **correct** code:

```rust
let len = "some string".len();
let b = "some string".is_empty();
```

## Further Reading

* [Clippy - needless_as_bytes](https://clippy.rust-lang.org/stable/index.html#needless_as_bytes)

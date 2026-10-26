Pattern: Missing use of `strip_prefix()`/`strip_suffix()`

Issue: -

## Description

Using `str:strip_{prefix,suffix}` is safer and may have better performance as there is no
slicing which may panic and the compiler does not need to insert this panic code. It is
also sometimes more readable as it removes the need for duplicating or storing the pattern
used by `str::{starts,ends}_with` and in the slicing.

## What it does

Suggests using `strip_{prefix,suffix}` over `str::{starts,ends}_with` and slicing using
the pattern's length.

## Examples

Example of **incorrect** code:

```rust
let s = "hello, world!";
if s.starts_with("hello, ") {
    assert_eq!(s["hello, ".len()..].to_uppercase(), "WORLD!");
}
```

Example of **correct** code:

```rust
let s = "hello, world!";
if let Some(end) = s.strip_prefix("hello, ") {
    assert_eq!(end.to_uppercase(), "WORLD!");
}
```

## Further Reading

* [Clippy - manual_strip](https://clippy.rust-lang.org/stable/index.html#manual_strip)

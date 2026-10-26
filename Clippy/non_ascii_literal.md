Pattern: Non-ASCII character in literal

Issue: -

## Description

Yeah, we know, the 90's called and wanted their charset
back. Even so, there still are editors and other programs out there that
don't work well with Unicode. So if the code is meant to be used
internationally, on multiple operating systems, or has other portability
requirements, activating this lint could be useful.

## What it does

Checks for non-ASCII characters in string and char literals.

## Examples

Example of **incorrect** code:

```rust
let x = String::from("€");
```

Example of **correct** code:

```rust
let x = String::from("\u{20ac}");
```

## Further Reading

* [Clippy - non_ascii_literal](https://clippy.rust-lang.org/stable/index.html#non_ascii_literal)

Pattern: Doc `include_str!` without `cfg(doc)`

Issue: -

## Description

These files are not useful for compilation but will still be included.
Also, if any of these non-source code file is updated, it will trigger a
recompilation.

## What it does

Checks if included files in doc comments are included only for `cfg(doc)`.

## Examples

Example of **incorrect** code:

```rust
#![doc = include_str!("some_file.md")]
```

Example of **correct** code:

```rust
#![cfg_attr(doc, doc = include_str!("some_file.md"))]
```

## Known problems

Excluding this will currently result in the file being left out if
the item's docs are inlined from another crate. This may be fixed in a
future version of rustdoc.

## Further Reading

* [Clippy - doc_include_without_cfg](https://clippy.rust-lang.org/stable/index.html#doc_include_without_cfg)

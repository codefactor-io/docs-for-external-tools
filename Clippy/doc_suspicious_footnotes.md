Pattern: Undefined footnote reference in docs

Issue: -

## Description

This probably means that a footnote was meant to exist,
but was not written.

## What it does

Detects syntax that looks like a footnote reference.

Rustdoc footnotes are compatible with GitHub-Flavored Markdown (GFM).
GFM does not parse a footnote reference unless its definition also
exists. This lint checks for footnote references with missing
definitions, unless it thinks you're writing a regex.

## Examples

Example of **incorrect** code:

```rust
/// This is not a footnote[^1], because no definition exists.
fn my_fn() {}
```

Example of **correct** code:

```rust
/// This is a footnote[^1].
///
/// [^1]: defined here
fn my_fn() {}
```

## Further Reading

* [Clippy - doc_suspicious_footnotes](https://clippy.rust-lang.org/stable/index.html#doc_suspicious_footnotes)

Pattern: Link reference definition in list or quote

Issue: -

## Description

This is probably intended as an intra-doc link. If it is really
supposed to be a reference definition, it can be written outside
of the list item or quote.

## What it does

Warns if a link reference definition appears at the start of a
list item or quote.

## Examples

Example of **incorrect** code:

```rust
//! - [link]: description
```

Example of **correct** code:

```rust
//! - [link][]: description (for intra-doc link)
//!
//! [link]: destination (for link reference definition)
```

## Further Reading

* [Clippy - doc_nested_refdefs](https://clippy.rust-lang.org/stable/index.html#doc_nested_refdefs)

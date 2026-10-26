Pattern: Long first doc paragraph

Issue: -

## Description

Documentation will show the first paragraph of the docstring in the summary page of a
module. Having a nice, short summary in the first paragraph is part of writing good docs.

## What it does

Checks if the first paragraph in the documentation of items listed in the module page is too long.

## Examples

Example of **incorrect** code:

```rust
/// A very short summary.
/// A much longer explanation that goes into a lot more detail about
/// how the thing works, possibly with doclinks and so one,
/// and probably spanning a many rows.
struct Foo {}
```

Example of **correct** code:

```rust
/// A very short summary.
///
/// A much longer explanation that goes into a lot more detail about
/// how the thing works, possibly with doclinks and so one,
/// and probably spanning a many rows.
struct Foo {}
```

## Further Reading

* [Clippy - too_long_first_doc_paragraph](https://clippy.rust-lang.org/stable/index.html#too_long_first_doc_paragraph)

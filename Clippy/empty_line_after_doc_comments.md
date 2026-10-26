Pattern: Empty line after doc comment

Issue: -

## Description

The doc comment may have meant to be an inner doc comment, regular
comment or applied to some old code that is now commented out. If it was
intended to be a doc comment, then the empty line should be removed.

## What it does

Checks for empty lines after doc comments.

## Examples

Example of **incorrect** code:

```rust
/// Some doc comment with a blank line after it.

fn f() {}

/// Docs for `old_code`
// fn old_code() {}

fn new_code() {}
```

Example of **correct** code:

```rust
//! Convert it to an inner doc comment

// Or a regular comment

/// Or remove the empty line
fn f() {}

// /// Docs for `old_code`
// fn old_code() {}

fn new_code() {}
```

## Further Reading

* [Clippy - empty_line_after_doc_comments](https://clippy.rust-lang.org/stable/index.html#empty_line_after_doc_comments)

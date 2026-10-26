Pattern: Outer doc comment followed by `!`

Issue: -

## Description

Triple-slash comments (known as "outer doc comments") apply to items that follow it.
An outer doc comment followed by a bang (i.e. `///!`) has no specific meaning.

The user most likely meant to write an inner doc comment (`//!`, `/*!`), which
applies to the parent item (i.e. the item that the comment is contained in,
usually a module or crate).

## What it does

Detects the use of outer doc comments (`///`, `/**`) followed by a bang (`!`): `///!`

## Examples

In this example, the doc comment is attached to the *function*, rather than the *module*.
```rust
pub mod util {
    ///! This module contains utility functions.

    pub fn dummy() {}
}
```

Use instead:
```rust
pub mod util {
    //! This module contains utility functions.

    pub fn dummy() {}
}
```

## Known problems

Inner doc comments can only appear before items, so there are certain cases where the suggestion
made by this lint is not valid code. For example:
```rust
fn foo() {}
///!
fn bar() {}
```
This lint detects the doc comment and suggests changing it to `//!`, but an inner doc comment
is not valid at that position.

## Further Reading

* [Clippy - suspicious_doc_comments](https://clippy.rust-lang.org/stable/index.html#suspicious_doc_comments)

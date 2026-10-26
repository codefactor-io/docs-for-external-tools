Pattern: Overindented list item in docs

Issue: -

## Description

Overindented list items in doc comments can lead to inconsistent and
poorly formatted documentation when rendered. Excessive indentation may
cause the text to be misinterpreted as a nested list item or code block,
affecting readability and the overall structure of the documentation.

## What it does

Detects overindented list items in doc comments where the continuation
lines are indented more than necessary.

## Examples

Example of **incorrect** code:

```rust
/// - This is the first item in a list
///      and this line is overindented.
```

Example of **correct** code:

```rust
/// - This is the first item in a list
///   and this line is overindented.
```

## Further Reading

* [Clippy - doc_overindented_list_items](https://clippy.rust-lang.org/stable/index.html#doc_overindented_list_items)

Pattern: Missing terminal punctuation in docs

Issue: -

## Description

A project may wish to enforce consistent doc comments by making sure paragraphs end with a
punctuation mark.

## What it does

Checks for doc comments whose paragraphs do not end with a period or another punctuation mark.
Various Markdowns constructs are taken into account to avoid false positives.

## Examples

Example of **incorrect** code:

```rust
/// Returns a random number
///
/// It was chosen by a fair dice roll
```

Example of **correct** code:

```rust
/// Returns a random number.
///
/// It was chosen by a fair dice roll.
```

## Terminal punctuation marks

This lint treats these characters as end markers: '.', '?', '!', '…' and ':'.

The colon is not exactly a terminal punctuation mark, but this is required for paragraphs that
introduce a table or a list for example.

## Further Reading

* [Clippy - doc_paragraphs_missing_punctuation](https://clippy.rust-lang.org/stable/index.html#doc_paragraphs_missing_punctuation)

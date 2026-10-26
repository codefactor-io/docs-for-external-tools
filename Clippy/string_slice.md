Pattern: String slicing

Issue: -

## Description

UTF-8 characters span multiple bytes, and it is easy to inadvertently confuse character
counts and string indices. This may lead to panics, and should warrant some test cases
containing wide UTF-8 characters. This lint is most useful in code that should avoid
panics at all costs.

## What it does

Checks for slice operations on strings

## Examples

Example of **incorrect** code:

```rust
&"Ölkanne"[1..];
```

## Known problems

Probably lots of false positives. If an index comes from a known valid position (e.g.
obtained via `char_indices` over the same string), it is totally OK.

## Further Reading

* [Clippy - string_slice](https://clippy.rust-lang.org/stable/index.html#string_slice)

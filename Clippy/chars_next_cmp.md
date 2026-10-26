Pattern: Missing use of `starts_with()` with char

Issue: -

## Description

Readability, this can be written more concisely as
`_.starts_with(_)`.

## What it does

Checks for usage of `.chars().next()` on a `str` to check
if it starts with a given char.

## Examples

Example of **incorrect** code:

```rust
let name = "foo";
if name.chars().next() == Some('_') {};
```

Example of **correct** code:

```rust
let name = "foo";
if name.starts_with('_') {};
```

## Further Reading

* [Clippy - chars_next_cmp](https://clippy.rust-lang.org/stable/index.html#chars_next_cmp)

Pattern: Missing use of `ends_with()` with char

Issue: -

## Description

Readability, this can be written more concisely as
`_.ends_with(_)`.

## What it does

Checks for usage of `_.chars().last()` or
`_.chars().next_back()` on a `str` to check if it ends with a given char.

## Examples

Example of **incorrect** code:

```rust
name.chars().last() == Some('_') || name.chars().next_back() == Some('-');
```

Example of **correct** code:

```rust
name.ends_with('_') || name.ends_with('-');
```

## Further Reading

* [Clippy - chars_last_cmp](https://clippy.rust-lang.org/stable/index.html#chars_last_cmp)

Pattern: Trimmed string split at hard-coded newline

Issue: -

## Description

Hard-coding the line endings makes the code less compatible. `str.lines` should be used instead.

## What it does

Checks for usages of `str.trim().split("\n")` and `str.trim().split("\r\n")`.

## Examples

Example of **incorrect** code:

```rust
"some\ntext\nwith\nnewlines\n".trim().split('\n');
```

Example of **correct** code:

```rust
"some\ntext\nwith\nnewlines\n".lines();
```

## Known Problems

This lint cannot detect if the split is intentionally restricted to a single type of newline (`"\n"` or
`"\r\n"`), for example during the parsing of a specific file format in which precisely one newline type is
valid.

## Further Reading

* [Clippy - str_split_at_newline](https://clippy.rust-lang.org/stable/index.html#str_split_at_newline)

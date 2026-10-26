Pattern: Unnecessary `trim()` before `split_whitespace()`

Issue: -

## Description

`split_whitespace` already ignores leading and trailing whitespace.

## What it does

Warns about calling `str::trim` (or variants) before `str::split_whitespace`.

## Examples

Example of **incorrect** code:

```rust
" A B C ".trim().split_whitespace();
```

Example of **correct** code:

```rust
" A B C ".split_whitespace();
```

## Further Reading

* [Clippy - trim_split_whitespace](https://clippy.rust-lang.org/stable/index.html#trim_split_whitespace)

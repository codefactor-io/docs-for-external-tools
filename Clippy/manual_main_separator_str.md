Pattern: Missing use of `MAIN_SEPARATOR_STR`

Issue: -

## Description

There exists a `std::path::MAIN_SEPARATOR_STR` which does not require
an extra memory allocation.

## What it does

Checks for references on `std::path::MAIN_SEPARATOR.to_string()` used
to build a `&str`.

## Examples

Example of **incorrect** code:

```rust
let s: &str = &std::path::MAIN_SEPARATOR.to_string();
```

Example of **correct** code:

```rust
let s: &str = std::path::MAIN_SEPARATOR_STR;
```

## Further Reading

* [Clippy - manual_main_separator_str](https://clippy.rust-lang.org/stable/index.html#manual_main_separator_str)

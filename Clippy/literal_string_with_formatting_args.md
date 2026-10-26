Pattern: Formatting argument in plain string literal

Issue: -

## Description

It will likely not generate the expected content.

## What it does

Checks if string literals have formatting arguments outside of macros
using them (like `format!`).

## Examples

Example of **incorrect** code:

```rust
let x: Option<usize> = None;
let y = "hello";
x.expect("{y:?}");
```

Example of **correct** code:

```rust
let x: Option<usize> = None;
let y = "hello";
x.expect(&format!("{y:?}"));
```

## Further Reading

* [Clippy - literal_string_with_formatting_args](https://clippy.rust-lang.org/stable/index.html#literal_string_with_formatting_args)

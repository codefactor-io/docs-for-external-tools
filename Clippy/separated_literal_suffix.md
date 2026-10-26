Pattern: Literal suffix separated by underscore

Issue: -

## Description

Suffix style should be consistent.

## What it does

Warns if literal suffixes are separated by an underscore.
To enforce separated literal suffix style,
see the `unseparated_literal_suffix` lint.

## Examples

Example of **incorrect** code:

```rust
123832_i32
```

Example of **correct** code:

```rust
123832i32
```

## Further Reading

* [Clippy - separated_literal_suffix](https://clippy.rust-lang.org/stable/index.html#separated_literal_suffix)

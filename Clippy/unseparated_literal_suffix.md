Pattern: Literal suffix without underscore

Issue: -

## Description

Suffix style should be consistent.

## What it does

Warns if literal suffixes are not separated by an
underscore.
To enforce unseparated literal suffix style,
see the `separated_literal_suffix` lint.

## Examples

Example of **incorrect** code:

```rust
123832i32
```

Example of **correct** code:

```rust
123832_i32
```

## Further Reading

* [Clippy - unseparated_literal_suffix](https://clippy.rust-lang.org/stable/index.html#unseparated_literal_suffix)

Pattern: Quotes instead of backticks in doc link

Issue: -

## Description

It is likely a typo when defining an intra-doc link

## What it does

Detects the syntax `['foo']` in documentation comments (notice quotes instead of backticks)
outside of code blocks

## Examples

Example of **incorrect** code:

```rust
/// See also: ['foo']
fn bar() {}
```

Example of **correct** code:

```rust
/// See also: [`foo`]
fn bar() {}
```

## Further Reading

* [Clippy - doc_link_with_quotes](https://clippy.rust-lang.org/stable/index.html#doc_link_with_quotes)

Pattern: Struct with empty brackets

Issue: -

## Description

Empty brackets after a struct declaration can be omitted,
and it may be desirable to do so consistently for style.

However, removing the brackets also introduces a public constant named after the struct,
so this is not just a syntactic simplification but an API change, and adding them back
is a *breaking* API change.

## What it does

Finds structs without fields (a so-called "empty struct") that are declared with brackets.

## Examples

Example of **incorrect** code:

```rust
struct Cookie {}
struct Biscuit();
```

Example of **correct** code:

```rust
struct Cookie;
struct Biscuit;
```

## Further Reading

* [Clippy - empty_structs_with_brackets](https://clippy.rust-lang.org/stable/index.html#empty_structs_with_brackets)

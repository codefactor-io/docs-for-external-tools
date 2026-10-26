Pattern: Single-character lifetime name

Issue: -

## Description

A single character is likely not enough to express the
purpose of a lifetime. Using a longer name can make code
easier to understand.

## What it does

Checks for lifetimes with names which are one character
long.

## Examples

Example of **incorrect** code:

```rust
struct DiagnosticCtx<'a> {
    source: &'a str,
}
```

Example of **correct** code:

```rust
struct DiagnosticCtx<'src> {
    source: &'src str,
}
```

## Known problems

Rust programmers and learning resources tend to use single
character lifetimes, so this lint is at odds with the
ecosystem at large. In addition, the lifetime's purpose may
be obvious or, rarely, expressible in one character.

## Further Reading

* [Clippy - single_char_lifetime_names](https://clippy.rust-lang.org/stable/index.html#single_char_lifetime_names)

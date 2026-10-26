Pattern: Overly complex boolean expression

Issue: -

## Description

Readability of boolean expressions suffers from
unnecessary duplication.

## What it does

Checks for boolean expressions that can be written more
concisely.

## Examples

Example of **incorrect** code:

```rust
if a && true {}
if !(a == b) {}
```

Example of **correct** code:

```rust
if a {}
if a != b {}
```

## Known problems

Ignores short circuiting behavior of `||` and
`&&`. Ignores `|`, `&` and `^`.

Creates a big toll on performance, **only enable sporadically**

## Further Reading

* [Clippy - nonminimal_bool](https://clippy.rust-lang.org/stable/index.html#nonminimal_bool)

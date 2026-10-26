Pattern: Boolean expression with redundant terms

Issue: -

## Description

This is most likely a logic bug.

## What it does

Checks for boolean expressions that contain terminals that
can be eliminated.

## Examples

Example of **incorrect** code:

```rust
// The `b` is unnecessary, the expression is equivalent to `if a`.
if a && b || a { ... }
```

Example of **correct** code:

```rust
if a {}
```

## Known problems

Ignores short circuiting behavior.
Creates a big toll on performance, **only enable sporadically**

## Further Reading

* [Clippy - overly_complex_bool_expr](https://clippy.rust-lang.org/stable/index.html#overly_complex_bool_expr)

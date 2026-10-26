Pattern: Collapsible `else if`

Issue: -

## Description

Each `if`-statement adds one level of nesting, which
makes code look more complex than it really is.

## What it does

Checks for collapsible `else { if ... }` expressions
that can be collapsed to `else if ...`.

## Examples

Example of **incorrect** code:

```rust

if x {
    …
} else {
    if y {
        …
    }
}
```

Example of **correct** code:

```rust
if x {
    …
} else if y {
    …
}
```

## Further Reading

* [Clippy - collapsible_else_if](https://clippy.rust-lang.org/stable/index.html#collapsible_else_if)

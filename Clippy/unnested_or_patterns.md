Pattern: Unnested or-pattern

Issue: -

## Description

In the example above, `Some` is repeated, which unnecessarily complicates the pattern.

## What it does

Checks for unnested or-patterns, e.g., `Some(0) | Some(2)` and
suggests replacing the pattern with a nested one, `Some(0 | 2)`.

Another way to think of this is that it rewrites patterns in
*disjunctive normal form (DNF)* into *conjunctive normal form (CNF)*.

## Examples

Example of **incorrect** code:

```rust
fn main() {
    if let Some(0) | Some(2) = Some(0) {}
}
```

Example of **correct** code:

```rust
fn main() {
    if let Some(0 | 2) = Some(0) {}
}
```

## Further Reading

* [Clippy - unnested_or_patterns](https://clippy.rust-lang.org/stable/index.html#unnested_or_patterns)

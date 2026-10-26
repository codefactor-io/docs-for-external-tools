Pattern: Unnecessary `..` in fully bound struct pattern

Issue: -

## Description

Correctness and readability. It's like having a wildcard pattern after
matching all enum variants explicitly.

## What it does

Checks for unnecessary '..' pattern binding on struct when all fields are explicitly matched.

## Examples

Example of **incorrect** code:

```rust
let a = A { a: 5 };

match a {
    A { a: 5, .. } => {},
    _ => {},
}
```

Example of **correct** code:

```rust
match a {
    A { a: 5 } => {},
    _ => {},
}
```

## Further Reading

* [Clippy - rest_pat_in_fully_bound_structs](https://clippy.rust-lang.org/stable/index.html#rest_pat_in_fully_bound_structs)

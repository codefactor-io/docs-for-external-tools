Pattern: Redundant `match` guard

Issue: -

## Description

It's more complex and much less readable. Making it part of the pattern can improve
exhaustiveness checking as well.

## What it does

Checks for unnecessary guards in match expressions.

## Examples

Example of **incorrect** code:

```rust
match x {
    Some(x) if matches!(x, Some(1)) => ..,
    Some(x) if x == Some(2) => ..,
    _ => todo!(),
}
```

Example of **correct** code:

```rust
match x {
    Some(Some(1)) => ..,
    Some(Some(2)) => ..,
    _ => todo!(),
}
```

## Further Reading

* [Clippy - redundant_guards](https://clippy.rust-lang.org/stable/index.html#redundant_guards)

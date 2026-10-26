Pattern: Redundant `name @ _` pattern

Issue: -

## Description

It's almost always more readable to just use direct
bindings.

## What it does

Checks for patterns in the form `name @ _`.

## Examples

Example of **incorrect** code:

```rust
match v {
    Some(x) => (),
    y @ _ => (),
}
```

Example of **correct** code:

```rust
match v {
    Some(x) => (),
    y => (),
}
```

## Further Reading

* [Clippy - redundant_pattern](https://clippy.rust-lang.org/stable/index.html#redundant_pattern)

Pattern: Wildcard in or-pattern

Issue: -

## Description

Wildcard pattern already covers any other pattern as it will match anyway.
It makes the code less readable, especially to spot wildcard pattern use in match arm.

## What it does

Checks for wildcard pattern used with others patterns in same match arm.

## Examples

Example of **incorrect** code:

```rust
match s {
    "a" => {},
    "bar" | _ => {},
}
```

Example of **correct** code:

```rust
match s {
    "a" => {},
    _ => {},
}
```

## Further Reading

* [Clippy - wildcard_in_or_patterns](https://clippy.rust-lang.org/stable/index.html#wildcard_in_or_patterns)

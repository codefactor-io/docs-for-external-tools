Pattern: `match` with one arm and wildcard

Issue: -

## Description

Just readability – `if let` nests less than a `match`.

## What it does

Checks for matches with two arms where an `if let else` will
usually suffice.

## Examples

Using `match`:

```rust
match x {
    Some(ref foo) => bar(foo),
    _ => bar(&other_ref),
}
```

Using `if let` with `else`:

```rust
if let Some(ref foo) = x {
    bar(foo);
} else {
    bar(&other_ref);
}
```

## Known problems

Personal style preferences may differ.

## Further Reading

* [Clippy - single_match_else](https://clippy.rust-lang.org/stable/index.html#single_match_else)

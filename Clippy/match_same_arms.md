Pattern: Duplicate match arm body

Issue: -

## Description

This is probably a copy & paste error. If arm bodies
are the same on purpose, you can factor them
[using `|`](https://doc.rust-lang.org/book/patterns.html#multiple-patterns).

## What it does

Checks for `match` with identical arm bodies.

Note: Does not lint on wildcards if the `non_exhaustive_omitted_patterns_lint` feature is
enabled and disallowed.

## Examples

```rust
match foo {
    Bar => bar(),
    Quz => quz(),
    Baz => bar(), // <= oops
}
```

This should probably be
```rust
match foo {
    Bar => bar(),
    Quz => quz(),
    Baz => baz(), // <= fixed
}
```

or if the original code was not a typo:
```rust
match foo {
    Bar | Baz => bar(), // <= shows the intent better
    Quz => quz(),
}
```

## Further Reading

* [Clippy - match_same_arms](https://clippy.rust-lang.org/stable/index.html#match_same_arms)

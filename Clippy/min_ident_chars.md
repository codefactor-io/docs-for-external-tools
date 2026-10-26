Pattern: Too short identifier name

Issue: -

## Description

To improve readability by requiring that every variable has a name more specific than a single letter can be.

## What it does

Checks for identifiers which consist of a single character (or fewer than the configured threshold).

Note: This lint can be very noisy when enabled; it may be desirable to only enable it
temporarily.

## Examples

Example of **incorrect** code:

```rust
for m in movies {
    let title = m.t;
}
```

Example of **correct** code:

```rust
for movie in movies {
    let title = movie.title;
}
```

## Limitations

Trait implementations which use the same function or parameter name as the trait declaration will
not be warned about, even if the name is below the configured limit.

## Further Reading

* [Clippy - min_ident_chars](https://clippy.rust-lang.org/stable/index.html#min_ident_chars)

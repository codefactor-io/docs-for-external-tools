Pattern: Trivial regular expression

Issue: -

## Description

Matching the regex can likely be replaced by `==` or
`str::starts_with`, `str::ends_with` or `std::contains` or other `str`
methods.

## What it does

Checks for trivial [regex](https://crates.io/crates/regex)
creation (with `Regex::new`, `RegexBuilder::new`, or `RegexSet::new`).

## Examples

Example of **incorrect** code:

```rust
Regex::new("^foobar")
```

Example of **correct** code:

```rust
str::starts_with("foobar")
```

## Known problems

If the same regex is going to be applied to multiple
inputs, the precomputations done by `Regex` construction can give
significantly better performance than any of the `str`-based methods.

## Further Reading

* [Clippy - trivial_regex](https://clippy.rust-lang.org/stable/index.html#trivial_regex)

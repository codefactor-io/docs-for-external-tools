Pattern: Invalid regular expression

Issue: -

## Description

This will lead to a runtime panic.

## What it does

Checks [regex](https://crates.io/crates/regex) creation
(with `Regex::new`, `RegexBuilder::new`, or `RegexSet::new`) for correct
regex syntax.

## Examples

Example of **incorrect** code:

```rust
Regex::new("(")
```

Example of **correct** code:

```rust
Regex::new("\(")
```

## Further Reading

* [Clippy - invalid_regex](https://clippy.rust-lang.org/stable/index.html#invalid_regex)

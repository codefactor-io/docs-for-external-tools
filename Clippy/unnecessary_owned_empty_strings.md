Pattern: Unnecessary owned empty string

Issue: -

## Description

This results in longer and less readable code

## What it does

Detects cases of owned empty strings being passed as an argument to a function expecting `&str`

## Examples

Example of **incorrect** code:

```rust
vec!["1", "2", "3"].join(&String::new());
```

Example of **correct** code:

```rust
vec!["1", "2", "3"].join("");
```

## Further Reading

* [Clippy - unnecessary_owned_empty_strings](https://clippy.rust-lang.org/stable/index.html#unnecessary_owned_empty_strings)

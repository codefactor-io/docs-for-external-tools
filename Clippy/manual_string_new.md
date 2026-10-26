Pattern: Missing use of `String::new()`

Issue: -

## Description

Different ways of creating an empty string makes your code less standardized, which can
be confusing.

## What it does

Checks for usage of `""` to create a `String`, such as `"".to_string()`, `"".to_owned()`,
`String::from("")` and others.

## Examples

Example of **incorrect** code:

```rust
let a = "".to_string();
let b: String = "".into();
```

Example of **correct** code:

```rust
let a = String::new();
let b = String::new();
```

## Further Reading

* [Clippy - manual_string_new](https://clippy.rust-lang.org/stable/index.html#manual_string_new)

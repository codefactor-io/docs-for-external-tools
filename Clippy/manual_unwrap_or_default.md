Pattern: Missing use of `unwrap_or_default()`

Issue: -

## Description

It can be done in one call with `.unwrap_or_default()`.

## What it does

Checks if a `match` or `if let` expression can be simplified using
`.unwrap_or_default()`.

## Examples

Example of **incorrect** code:

```rust
let x: Option<String> = Some(String::new());
let y: String = match x {
    Some(v) => v,
    None => String::new(),
};

let x: Option<Vec<String>> = Some(Vec::new());
let y: Vec<String> = if let Some(v) = x {
    v
} else {
    Vec::new()
};
```

Example of **correct** code:

```rust
let x: Option<String> = Some(String::new());
let y: String = x.unwrap_or_default();

let x: Option<Vec<String>> = Some(Vec::new());
let y: Vec<String> = x.unwrap_or_default();
```

## Further Reading

* [Clippy - manual_unwrap_or_default](https://clippy.rust-lang.org/stable/index.html#manual_unwrap_or_default)

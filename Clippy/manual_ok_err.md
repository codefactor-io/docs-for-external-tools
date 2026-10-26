Pattern: Missing use of `Result::ok()` or `Result::err()`

Issue: -

## Description

Using `.ok()` or `.err()` rather than a `match` or
`if let` is less complex and more readable.

## What it does

Checks for manual implementation of `.ok()` or `.err()`
on `Result` values.

## Examples

Example of **incorrect** code:

```rust
let a = match func() {
    Ok(v) => Some(v),
    Err(_) => None,
};
let b = if let Err(v) = func() {
    Some(v)
} else {
    None
};
```

Example of **correct** code:

```rust
let a = func().ok();
let b = func().err();
```

## Further Reading

* [Clippy - manual_ok_err](https://clippy.rust-lang.org/stable/index.html#manual_ok_err)

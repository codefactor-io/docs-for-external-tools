Pattern: Use of `to_string()` on `&str`

Issue: -

## Description

The `to_string` method is also used on other types to convert them to a string.
When called on a `&str` it turns the `&str` into the owned variant `String`, which can be
more specifically expressed with `.to_owned()`.

## What it does

This lint checks for `.to_string()` method calls on values of type `&str`.

## Examples

Example of **incorrect** code:

```rust
let _ = "str".to_string();
```

Example of **correct** code:

```rust
let _ = "str".to_owned();
```

## Further Reading

* [Clippy - str_to_string](https://clippy.rust-lang.org/stable/index.html#str_to_string)

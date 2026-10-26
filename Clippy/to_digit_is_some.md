Pattern: Missing use of `char::is_digit()`

Issue: -

## Description

This is a convoluted way of checking if a `char` is a digit. It's
more straight forward to use the dedicated `is_digit` method.

## What it does

Checks for `.to_digit(..).is_some()` on `char`s.

## Examples

Example of **incorrect** code:

```rust
let is_digit = c.to_digit(radix).is_some();
```

Example of **correct** code:

```rust
let is_digit = c.is_digit(radix);
```

## Further Reading

* [Clippy - to_digit_is_some](https://clippy.rust-lang.org/stable/index.html#to_digit_is_some)

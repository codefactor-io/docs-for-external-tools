Pattern: Missing use of `Result::expect_err()`

Issue: -

## Description

`.expect_err()` can be called directly to avoid the extra type conversion from `err()`.

## What it does

Checks for `.err().expect()` calls on the `Result` type.

## Examples

Example of **incorrect** code:

```rust
let x: Result<u32, &str> = Ok(10);
x.err().expect("Testing err().expect()");
```

Example of **correct** code:

```rust
let x: Result<u32, &str> = Ok(10);
x.expect_err("Testing expect_err");
```

## Further Reading

* [Clippy - err_expect](https://clippy.rust-lang.org/stable/index.html#err_expect)

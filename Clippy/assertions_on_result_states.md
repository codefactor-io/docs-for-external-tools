Pattern: Assertion on `is_ok()` or `is_err()`

Issue: -

## Description

This form of assertion does not show any of the information present in the `Result`
other than which variant it isn’t.

## What it does

Checks for `assert!(r.is_ok())` or `assert!(r.is_err())` calls.

## Examples

Example of **incorrect** code:

```rust
assert!(r.is_ok());
assert!(r.is_err());
```

Example of **correct** code:

```rust
r.unwrap();
r.unwrap_err();
```

## Known problems

The suggested replacement decreases the readability of code and log output.

## Further Reading

* [Clippy - assertions_on_result_states](https://clippy.rust-lang.org/stable/index.html#assertions_on_result_states)

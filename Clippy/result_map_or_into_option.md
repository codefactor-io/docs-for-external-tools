Pattern: Missing use of `Result::ok()`

Issue: -

## Description

Readability, this can be written more concisely as
`_.ok()`.

## What it does

Checks for usage of `_.map_or(None, Some)`.

## Examples

Example of **incorrect** code:

```rust
assert_eq!(Some(1), r.map_or(None, Some));
```

Example of **correct** code:

```rust
assert_eq!(Some(1), r.ok());
```

## Further Reading

* [Clippy - result_map_or_into_option](https://clippy.rust-lang.org/stable/index.html#result_map_or_into_option)

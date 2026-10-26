Pattern: Redundant `as_str()`

Issue: -

## Description

The `as_str()` conversion is pointless and can be removed for simplicity and cleanliness.

## What it does

Checks for usage of `as_str()` on a `String` chained with a method available on the `String` itself.

## Examples

Example of **incorrect** code:

```rust
let owned_string = "This is a string".to_owned();
owned_string.as_str().as_bytes()
```

Example of **correct** code:

```rust
let owned_string = "This is a string".to_owned();
owned_string.as_bytes()
```

## Further Reading

* [Clippy - redundant_as_str](https://clippy.rust-lang.org/stable/index.html#redundant_as_str)

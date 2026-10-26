Pattern: Missing use of `str::is_ascii()`

Issue: -

## Description

The `str` type already implements the `is_ascii` method.

## What it does

Checks if an iterator is used to check if a string is ascii.

## Examples

Example of **incorrect** code:

```rust
"foo".chars().all(|c| c.is_ascii());
```

Example of **correct** code:

```rust
"foo".is_ascii();
```

## Further Reading

* [Clippy - needless_character_iteration](https://clippy.rust-lang.org/stable/index.html#needless_character_iteration)

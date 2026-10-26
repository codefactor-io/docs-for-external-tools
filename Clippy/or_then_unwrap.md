Pattern: Use of `or().unwrap()`

Issue: -

## Description

You should use `.unwrap_or(…)` instead for clarity.

## What it does

Checks for `.or(…).unwrap()` calls to Options and Results.

## Examples

Example of **incorrect** code:

```rust
// Result
let value = result.or::<Error>(Ok(fallback)).unwrap();

// Option
let value = option.or(Some(fallback)).unwrap();
```

Example of **correct** code:

```rust
// Result
let value = result.unwrap_or(fallback);

// Option
let value = option.unwrap_or(fallback);
```

## Further Reading

* [Clippy - or_then_unwrap](https://clippy.rust-lang.org/stable/index.html#or_then_unwrap)

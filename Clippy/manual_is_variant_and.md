Pattern: Missing use of `is_some_and()` or `is_ok_and()`

Issue: -

## Description

Readability. These can be written more concisely as `option.is_some_and(f)` and `result.is_ok_and(f)`.

## What it does

Checks for usage of `option.map(f).unwrap_or_default()` and `result.map(f).unwrap_or_default()` where `f` is a function or closure that returns the `bool` type.

Also checks for equality comparisons like `option.map(f) == Some(true)` and `result.map(f) == Ok(true)`,
as well as `result.ok().is_some_and(f)`.

## Examples

Example of **incorrect** code:

```rust
option.map(|a| a > 10).unwrap_or_default();
result.map(|a| a > 10).unwrap_or_default();

option.map(|a| a > 10) == Some(true);
result.map(|a| a > 10) == Ok(true);
option.map(|a| a > 10) != Some(true);
result.map(|a| a > 10) != Ok(true);

result.ok().is_some_and(|a| a > 10);
```

Example of **correct** code:

```rust
option.is_some_and(|a| a > 10);
result.is_ok_and(|a| a > 10);

option.is_some_and(|a| a > 10);
result.is_ok_and(|a| a > 10);
option.is_none_or(|a| a > 10);
!result.is_ok_and(|a| a > 10);

result.is_ok_and(|a| a > 10);
```

## Further Reading

* [Clippy - manual_is_variant_and](https://clippy.rust-lang.org/stable/index.html#manual_is_variant_and)

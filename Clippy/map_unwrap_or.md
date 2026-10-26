Pattern: Missing use of `map_or()` or `map_or_else()`

Issue: -

## Description

Readability, these can be written more concisely (resp.) as
`option.map_or(_, _)`, `option.map_or_else(_, _)` and `result.map_or_else(_, _)`.

## What it does

Checks for usage of `option.map(_).unwrap_or(_)` or `option.map(_).unwrap_or_else(_)` or
`result.map(_).unwrap_or_else(_)`.

## Examples

Example of **incorrect** code:

```rust
option.map(|a| a + 1).unwrap_or(0);
option.map(|a| a > 10).unwrap_or(false);
result.map(|a| a + 1).unwrap_or_else(some_function);
```

Example of **correct** code:

```rust
option.map_or(0, |a| a + 1);
option.is_some_and(|a| a > 10);
result.map_or_else(some_function, |a| a + 1);
```

## Known problems

The order of the arguments is not in execution order

## Further Reading

* [Clippy - map_unwrap_or](https://clippy.rust-lang.org/stable/index.html#map_unwrap_or)

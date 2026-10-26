Pattern: Missing use of `try_for_each()`

Issue: -

## Description

Using `try_for_each` instead is more readable and idiomatic.

## What it does

Checks for usage of `_.map(_).collect::<Result<(), _>()`.

## Examples

Example of **incorrect** code:

```rust
(0..3).map(|t| Err(t)).collect::<Result<(), _>>();
```

Example of **correct** code:

```rust
(0..3).try_for_each(|t| Err(t));
```

## Further Reading

* [Clippy - map_collect_result_unit](https://clippy.rust-lang.org/stable/index.html#map_collect_result_unit)

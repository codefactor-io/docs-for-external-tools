Pattern: Use of `and_then()` instead of `map()`

Issue: -

## Description

This can be written more concisely as `_.map(|x| y)` or `_.map_err(|x| y)`.

## What it does

Checks for usage of `_.and_then(|x| Some(y))`, `_.and_then(|x| Ok(y))`
or `_.or_else(|x| Err(y))`.

## Examples

Example of **incorrect** code:

```rust
let _ = opt().and_then(|s| Some(s.len()));
let _ = res().and_then(|s| if s.len() == 42 { Ok(10) } else { Ok(20) });
let _ = res().or_else(|s| if s.len() == 42 { Err(10) } else { Err(20) });
```

Example of **correct** code:

```rust
let _ = opt().map(|s| s.len());
let _ = res().map(|s| if s.len() == 42 { 10 } else { 20 });
let _ = res().map_err(|s| if s.len() == 42 { 10 } else { 20 });
```

## Further Reading

* [Clippy - bind_instead_of_map](https://clippy.rust-lang.org/stable/index.html#bind_instead_of_map)

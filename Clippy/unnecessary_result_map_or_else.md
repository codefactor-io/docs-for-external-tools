Pattern: Identity closure in `Result::map_or_else()`

Issue: -

## Description

This can be written more concisely by using `unwrap_or_else()`.

## What it does

Checks for usage of `.map_or_else()` "map closure" for `Result` type.

## Examples

Example of **incorrect** code:

```rust
let x: Result<u32, ()> = Ok(0);
let y = x.map_or_else(|err| handle_error(err), |n| n);
```

Example of **correct** code:

```rust
let x: Result<u32, ()> = Ok(0);
let y = x.unwrap_or_else(|err| handle_error(err));
```

## Further Reading

* [Clippy - unnecessary_result_map_or_else](https://clippy.rust-lang.org/stable/index.html#unnecessary_result_map_or_else)

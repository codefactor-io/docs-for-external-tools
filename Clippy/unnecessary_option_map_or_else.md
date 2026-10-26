Pattern: Identity closure in `Option::map_or_else()`

Issue: -

## Description

This can be written more concisely by using `unwrap_or_else()`.

## What it does

Checks for usage of `.map_or_else()` "map closure" for `Option` type.

## Examples

Example of **incorrect** code:

```rust
let k = 10;
let x: Option<u32> = Some(4);
let y = x.map_or_else(|| 2 * k, |n| n);
```

Example of **correct** code:

```rust
let k = 10;
let x: Option<u32> = Some(4);
let y = x.unwrap_or_else(|| 2 * k);
```

## Further Reading

* [Clippy - unnecessary_option_map_or_else](https://clippy.rust-lang.org/stable/index.html#unnecessary_option_map_or_else)

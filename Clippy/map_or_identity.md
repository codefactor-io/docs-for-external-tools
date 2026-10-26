Pattern: Use of identity function in `map_or()`

Issue: -

## Description

This can be written more concisely by using `unwrap_or()`.

## What it does

Checks the usage of `.map_or(...)` with an identity function for `Option` and `Result` types.

## Examples

Example of **incorrect** code:

```rust
let opt = Some(1);
opt.map_or(42, |v| v);
```

Example of **correct** code:

```rust
let opt = Some(1);
opt.unwrap_or(42);
```

## Further Reading

* [Clippy - map_or_identity](https://clippy.rust-lang.org/stable/index.html#map_or_identity)

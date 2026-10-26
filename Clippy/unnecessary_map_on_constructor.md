Pattern: Unnecessary `map()` on constructor

Issue: -

## Description

It introduces unnecessary complexity. Instead, the function can be called before
constructing the `Option` or `Result` from its return value.

## What it does

Suggests removing the use of a `map()` (or `map_err()`) method when an `Option` or `Result`
is being constructed.

## Examples

Example of **incorrect** code:

```rust
Some(4).map(i32::swap_bytes)
```

Example of **correct** code:

```rust
Some(i32::swap_bytes(4))
```

## Further Reading

* [Clippy - unnecessary_map_on_constructor](https://clippy.rust-lang.org/stable/index.html#unnecessary_map_on_constructor)

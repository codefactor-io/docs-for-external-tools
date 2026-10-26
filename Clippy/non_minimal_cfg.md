Pattern: `cfg` combinator with one condition

Issue: -

## Description

If there is only one condition, no need to wrap it into `any` or `all` combinators.

## What it does

Checks for `any` and `all` combinators in `cfg` with only one condition.

## Examples

Example of **incorrect** code:

```rust
#[cfg(any(unix))]
pub struct Bar;
```

Example of **correct** code:

```rust
#[cfg(unix)]
pub struct Bar;
```

## Further Reading

* [Clippy - non_minimal_cfg](https://clippy.rust-lang.org/stable/index.html#non_minimal_cfg)

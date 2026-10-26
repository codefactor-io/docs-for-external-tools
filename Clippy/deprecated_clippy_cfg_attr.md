Pattern: Deprecated tool `feature` check in `cfg`

Issue: -

## Description

This feature has been deprecated for years and shouldn't be used anymore.

## What it does

Checks for `#[cfg_attr(feature = "cargo-clippy", ...)]` and for
`#[cfg(feature = "cargo-clippy")]` and suggests to replace it with
`#[cfg_attr(clippy, ...)]` or `#[cfg(clippy)]`.

## Examples

Example of **incorrect** code:

```rust
#[cfg(feature = "cargo-clippy")]
struct Bar;
```

Example of **correct** code:

```rust
#[cfg(clippy)]
struct Bar;
```

## Further Reading

* [Clippy - deprecated_clippy_cfg_attr](https://clippy.rust-lang.org/stable/index.html#deprecated_clippy_cfg_attr)

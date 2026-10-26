Pattern: Unnecessary `cfg_attr` wrapper around `allow`

Issue: -

## Description

There is no reason to put clippy attributes behind a clippy `cfg` as they are not
run by anything else than clippy.

## What it does

Checks for `#[cfg_attr(clippy, allow(clippy::lint))]`
and suggests to replace it with `#[allow(clippy::lint)]`.

## Examples

Example of **incorrect** code:

```rust
#![cfg_attr(clippy, allow(clippy::deprecated_cfg_attr))]
```

Example of **correct** code:

```rust
#![allow(clippy::deprecated_cfg_attr)]
```

## Further Reading

* [Clippy - unnecessary_clippy_cfg](https://clippy.rust-lang.org/stable/index.html#unnecessary_clippy_cfg)

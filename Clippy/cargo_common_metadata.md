Pattern: Missing common metadata in `Cargo.toml`

Issue: -

## Description

It will be more difficult for users to discover the
purpose of the crate, and key information related to it.

## What it does

Checks to see if all common metadata is defined in
`Cargo.toml`. See: <https://rust-lang.github.io/api-guidelines/documentation.html#cargotoml-includes-all-common-metadata-c-metadata>

## Examples

```toml
# This `Cargo.toml` is missing a description field:
[package]
name = "clippy"
version = "0.0.212"
repository = "https://github.com/rust-lang/rust-clippy"
readme = "README.md"
license = "MIT OR Apache-2.0"
keywords = ["clippy", "lint", "plugin"]
categories = ["development-tools", "development-tools::cargo-plugins"]
```

Should include a description field like:

```toml
# This `Cargo.toml` includes all common metadata
[package]
name = "clippy"
version = "0.0.212"
description = "A bunch of helpful lints to avoid common pitfalls in Rust"
repository = "https://github.com/rust-lang/rust-clippy"
readme = "README.md"
license = "MIT OR Apache-2.0"
keywords = ["clippy", "lint", "plugin"]
categories = ["development-tools", "development-tools::cargo-plugins"]
```

## Further Reading

* [Clippy - cargo_common_metadata](https://clippy.rust-lang.org/stable/index.html#cargo_common_metadata)

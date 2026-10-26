Pattern: Wildcard dependency version

Issue: -

## Description

[As the edition guide says](https://rust-lang-nursery.github.io/edition-guide/rust-2018/cargo-and-crates-io/crates-io-disallows-wildcard-dependencies.html),
it is highly unlikely that you work with any possible version of your dependency,
and wildcard dependencies would cause unnecessary breakage in the ecosystem.

## What it does

Checks for wildcard dependencies in the `Cargo.toml`.

## Examples

Example of **incorrect** code:

```toml
[dependencies]
regex = "*"
```

Example of **correct** code:

```toml
[dependencies]
# allow patch updates, but not minor or major version changes
some_crate_1 = "~1.2.3"

# pin the version to a specific version
some_crate_2 = "=1.2.3"
```

## Further Reading

* [Clippy - wildcard_dependencies](https://clippy.rust-lang.org/stable/index.html#wildcard_dependencies)

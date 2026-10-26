Pattern: Multiple versions of the same crate

Issue: -

## Description

This bloats the size of targets, and can lead to
confusing error messages when structs or traits are used interchangeably
between different versions of a crate.

## What it does

Checks to see if multiple versions of a crate are being
used.

## Examples

Example of **incorrect** code:

```toml
# This will pull in both winapi v0.3.x and v0.2.x, triggering a warning.
[dependencies]
ctrlc = "=3.1.0"
ansi_term = "=0.11.0"
```

## Known problems

Because this can be caused purely by the dependencies
themselves, it's not always possible to fix this issue.
In those cases, you can allow that specific crate using
the `allowed-duplicate-crates` configuration option.

## Further Reading

* [Clippy - multiple_crate_versions](https://clippy.rust-lang.org/stable/index.html#multiple_crate_versions)

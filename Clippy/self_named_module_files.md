Pattern: Module layout without `mod.rs`

Issue: -

## Description

Having multiple module layout styles in a project can be confusing.

## What it does

Checks that module layout uses only `mod.rs` files.

## Examples

Example of **incorrect** code:

```text
src/
  stuff/
    stuff_files.rs
  stuff.rs
  lib.rs
```

Example of **correct** code:

```text
src/
  stuff/
    stuff_files.rs
    mod.rs
  lib.rs
```

## Further Reading

* [Clippy - self_named_module_files](https://clippy.rust-lang.org/stable/index.html#self_named_module_files)

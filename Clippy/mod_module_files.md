Pattern: Use of `mod.rs` module file

Issue: -

## Description

Having multiple module layout styles in a project can be confusing.

## What it does

Checks that module layout uses only self named module files; bans `mod.rs` files.

## Examples

Example of **incorrect** code:

```text
src/
  stuff/
    stuff_files.rs
    mod.rs
  lib.rs
```

Example of **correct** code:

```text
src/
  stuff/
    stuff_files.rs
  stuff.rs
  lib.rs
```

## Further Reading

* [Clippy - mod_module_files](https://clippy.rust-lang.org/stable/index.html#mod_module_files)

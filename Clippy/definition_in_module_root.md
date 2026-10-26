Pattern: Definition in `mod.rs`

Issue: -

## Description

`mod.rs` is well-suited to acting as a table of contents — listing
submodules and re-exports while leaving definitions to named files.
Naming each file after its primary definition keeps filenames
descriptive and unique, makes editor tabs and search results easier
to scan, and makes the filesystem tree mirror the module tree, so
the file layout is uniquely determined by the module structure.

## What it does

Checks for definitions (structs, functions, traits, etc.) in `mod.rs`
files. `lib.rs` and `main.rs` are not checked.

## Examples

Example of **incorrect** code:

```rust
// stuff/mod.rs
mod bar;
pub struct Foo { /* ... */ }
impl Foo { /* ... */ }
```

Example of **correct** code:

```rust
// stuff/mod.rs
mod bar;
mod foo;
pub use foo::Foo;

// stuff/foo.rs
pub struct Foo { /* ... */ }
impl Foo { /* ... */ }
```

## Notes

This lint is most useful alongside `self_named_module_files`, which
requires `mod.rs` files; together they constrain `mod.rs` to
declarations only. Under `mod_module_files` (which forbids `mod.rs`
entirely) this lint has nothing to fire on.

If a definition's name matches its parent module's name, moving it
produces `foo/foo.rs`, which `module_inception` flags — projects
in that situation typically also `allow(module_inception)`.

## Further Reading

* [Clippy - definition_in_module_root](https://clippy.rust-lang.org/stable/index.html#definition_in_module_root)

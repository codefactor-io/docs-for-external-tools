Pattern: Use of inline module

Issue: -

## Description

Having multiple module layout styles in a project can be confusing.

## What it does

Checks that module layout does not use inline modules.
Inline test modules (anything annotated with `#[cfg(test)]`) are not linted.

## Examples

Example of **incorrect** code:

```rust
// in `src/lib.rs`
mod foo {
   /* module contents */
}
```

Example of **correct** code:

```rust
// in `src/lib.rs`
mod foo;
// in `src/foo.rs` (or `src/foo/mod.rs`)
/* module contents */
```

## Known problems

The lint currently doesn't lint inline modules whose parent module is annotated
with the `#[path]` attribute.

## Further Reading

* [Clippy - inline_modules](https://clippy.rust-lang.org/stable/index.html#inline_modules)

Pattern: File extension check with `Path::ends_with()`

Issue: -

## Description

This doesn't actually compare file extensions. Rather, `ends_with` compares the given argument
to the last **component** of the path and checks if it matches exactly.

## What it does

Looks for calls to `Path::ends_with` calls where the argument looks like a file extension.

By default, Clippy has a short list of known filenames that start with a dot
but aren't necessarily file extensions (e.g. the `.git` folder), which are allowed by default.
The `allowed-dotfiles` configuration can be used to allow additional
file extensions that Clippy should not lint.

## Examples

Example of **incorrect** code:

```rust
fn is_markdown(path: &Path) -> bool {
    path.ends_with(".md")
}
```

Example of **correct** code:

```rust
fn is_markdown(path: &Path) -> bool {
    path.extension().is_some_and(|ext| ext == "md")
}
```

## Known issues

File extensions are often at most three characters long, so this only lints in those cases
in an attempt to avoid false positives.
Any extension names longer than that are assumed to likely be real path components and are
therefore ignored.

## Further Reading

* [Clippy - path_ends_with_ext](https://clippy.rust-lang.org/stable/index.html#path_ends_with_ext)

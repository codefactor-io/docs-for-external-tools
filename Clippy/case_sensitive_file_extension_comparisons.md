Pattern: Case-sensitive file extension comparison

Issue: -

## Description

`ends_with` is case-sensitive and may not detect files with a valid extension.

## What it does

Checks for calls to `ends_with` with possible file extensions
and suggests to use a case-insensitive approach instead.

## Examples

Example of **incorrect** code:

```rust
fn is_rust_file(filename: &str) -> bool {
    filename.ends_with(".rs")
}
```

Example of **correct** code:

```rust
fn is_rust_file(filename: &str) -> bool {
    let filename = std::path::Path::new(filename);
    filename.extension()
        .map_or(false, |ext| ext.eq_ignore_ascii_case("rs"))
}
```

## Further Reading

* [Clippy - case_sensitive_file_extension_comparisons](https://clippy.rust-lang.org/stable/index.html#case_sensitive_file_extension_comparisons)

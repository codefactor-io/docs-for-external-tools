Pattern: Use of `FileType::is_file()`

Issue: -

## Description

When people testing a file type with `FileType::is_file`
they are testing whether a path is something they can get bytes from. But
`is_file` doesn't cover special file types in unix-like systems, and doesn't cover
symlink in windows. Using `!FileType::is_dir()` is a better way to that intention.

## What it does

Checks for `FileType::is_file()`.

## Examples

Example of **incorrect** code:

```rust
let metadata = std::fs::metadata("foo.txt")?;
let filetype = metadata.file_type();

if filetype.is_file() {
    // read file
}
```

Example of **correct** code:

```rust
let metadata = std::fs::metadata("foo.txt")?;
let filetype = metadata.file_type();

if !filetype.is_dir() {
    // read file
}
```

## Further Reading

* [Clippy - filetype_is_file](https://clippy.rust-lang.org/stable/index.html#filetype_is_file)

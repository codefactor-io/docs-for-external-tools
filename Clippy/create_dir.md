Pattern: Use of `fs::create_dir()`

Issue: -

## Description

Sometimes `std::fs::create_dir` is mistakenly chosen over `std::fs::create_dir_all`,
resulting in failure when more than one directory needs to be created or when the directory already exists.
Crates which never need to specifically create a single directory may wish to prevent this mistake.

## What it does

Checks usage of `std::fs::create_dir` and suggest using `std::fs::create_dir_all` instead.

## Examples

Example of **incorrect** code:

```rust
std::fs::create_dir("foo");
```

Example of **correct** code:

```rust
std::fs::create_dir_all("foo");
```

## Further Reading

* [Clippy - create_dir](https://clippy.rust-lang.org/stable/index.html#create_dir)

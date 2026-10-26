Pattern: Public field with underscore prefix

Issue: -

## Description

Fields prefixed with an `_` are inferred as unused, which suggests it should not be marked
as `pub`, because marking it as `pub` infers it will be used.

## What it does

Checks whether any field of the struct is prefixed with an `_` (underscore) and also marked
`pub` (public)

## Examples

```rust
struct FileHandle {
    pub _descriptor: usize,
}
```
Use instead:
```rust
struct FileHandle {
    _descriptor: usize,
}
```

OR

```rust
struct FileHandle {
    pub descriptor: usize,
}
```

## Further Reading

* [Clippy - pub_underscore_fields](https://clippy.rust-lang.org/stable/index.html#pub_underscore_fields)

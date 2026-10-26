Pattern: Missing `'static` lifetime on returned `&str`

Issue: -

## Description

This leaves the caller unable to use the `&str` as `&'static str`, causing unnecessary allocations or confusion.
This is also most likely what you meant to write.

## What it does

Detects functions that are written to return `&str` that could return `&'static str` but instead return a `&'a str`.

## Examples

```rust
impl MyType {
    fn returns_literal(&self) -> &str {
        "Literal"
    }
}
```
Use instead:
```rust
impl MyType {
    fn returns_literal(&self) -> &'static str {
        "Literal"
    }
}
```
Or, in case you may return a non-literal `str` in future:
```rust
impl MyType {
    fn returns_literal<'a>(&'a self) -> &'a str {
        "Literal"
    }
}
```

## Further Reading

* [Clippy - unnecessary_literal_bound](https://clippy.rust-lang.org/stable/index.html#unnecessary_literal_bound)

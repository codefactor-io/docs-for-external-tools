Pattern: Missing use of `flatten()` on `Result` items

Issue: -

## Description

`Result` implements `IntoIterator<Item = T>`. This means that `Result` can be flattened
automatically without suspicious-looking `unwrap` calls.

## What it does

Checks for iterators of `Result`s using `.filter(Result::is_ok).map(Result::unwrap)` that may
be replaced with a `.flatten()` call.

## Examples

Example of **incorrect** code:

```rust
let _ = std::iter::empty::<Result<i32, ()>>().filter(Result::is_ok).map(Result::unwrap);
```

Example of **correct** code:

```rust
let _ = std::iter::empty::<Result<i32, ()>>().flatten();
```

## Further Reading

* [Clippy - result_filter_map](https://clippy.rust-lang.org/stable/index.html#result_filter_map)

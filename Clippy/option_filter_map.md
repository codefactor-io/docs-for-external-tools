Pattern: Use of `filter(is_some).map(unwrap)`

Issue: -

## Description

`Option` is like a collection of 0-1 things, so `flatten`
automatically does this without suspicious-looking `unwrap` calls.

## What it does

Checks for iterators of `Option`s using `.filter(Option::is_some).map(Option::unwrap)` that may
be replaced with a `.flatten()` call.

## Examples

Example of **incorrect** code:

```rust
let _ = std::iter::empty::<Option<i32>>().filter(Option::is_some).map(Option::unwrap);
```

Example of **correct** code:

```rust
let _ = std::iter::empty::<Option<i32>>().flatten();
```

## Further Reading

* [Clippy - option_filter_map](https://clippy.rust-lang.org/stable/index.html#option_filter_map)

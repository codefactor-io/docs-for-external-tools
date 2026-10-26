Pattern: Missing use of `Iterator::find_map()`

Issue: -

## Description

Readability, this can be written more concisely as
`_.find_map(_)`.

## What it does

Checks for usage of `_.filter_map(_).next()`.

## Examples

Example of **incorrect** code:

```rust
 (0..3).filter_map(|x| if x == 2 { Some(x) } else { None }).next();
```

Example of **correct** code:

```rust
 (0..3).find_map(|x| if x == 2 { Some(x) } else { None });
```

## Further Reading

* [Clippy - filter_map_next](https://clippy.rust-lang.org/stable/index.html#filter_map_next)

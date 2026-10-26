Pattern: Use of `filter_map()` with identity closure

Issue: -

## Description

Readability, this can be written more concisely by using `flatten`.

## What it does

Checks for usage of `filter_map(|x| x)`.

## Examples

Example of **incorrect** code:

```rust
iter.filter_map(|x| x);
```

Example of **correct** code:

```rust
iter.flatten();
```

## Further Reading

* [Clippy - filter_map_identity](https://clippy.rust-lang.org/stable/index.html#filter_map_identity)

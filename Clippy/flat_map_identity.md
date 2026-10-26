Pattern: Use of `flat_map()` with identity closure

Issue: -

## Description

Readability, this can be written more concisely by using `flatten`.

## What it does

Checks for usage of `flat_map(|x| x)`.

## Examples

Example of **incorrect** code:

```rust
iter.flat_map(|x| x);
```

Example of **correct** code:

```rust
iter.flatten();
```

## Further Reading

* [Clippy - flat_map_identity](https://clippy.rust-lang.org/stable/index.html#flat_map_identity)

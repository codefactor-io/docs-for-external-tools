Pattern: Missing use of `cloned()` or `copied()`

Issue: -

## Description

Readability, this can be written more concisely

## What it does

Checks for usage of `map(|x| x.clone())` or
dereferencing closures for `Copy` types, on `Iterator` or `Option`,
and suggests `cloned()` or `copied()` instead

## Examples

Example of **incorrect** code:

```rust
let x = vec![42, 43];
let y = x.iter();
let z = y.map(|i| *i);
```

Example of **correct** code:

```rust
let x = vec![42, 43];
let y = x.iter();
let z = y.cloned();
```

## Further Reading

* [Clippy - map_clone](https://clippy.rust-lang.org/stable/index.html#map_clone)

Pattern: Slice binding used only for indexing

Issue: -

## Description

Accessing slice values using indices can lead to panics. Using refutable
patterns can avoid these. Binding to individual values also improves the
readability as they can be named.

## What it does

The lint checks for slice bindings in patterns that are only used to
access individual slice values.

## Examples

Example of **incorrect** code:

```rust
let slice: Option<&[u32]> = Some(&[1, 2, 3]);

if let Some(slice) = slice {
    println!("{}", slice[0]);
}
```

Example of **correct** code:

```rust
let slice: Option<&[u32]> = Some(&[1, 2, 3]);

if let Some(&[first, ..]) = slice {
    println!("{}", first);
}
```

## Limitations

This lint currently only checks for immutable access inside `if let`
patterns.

## Further Reading

* [Clippy - index_refutable_slice](https://clippy.rust-lang.org/stable/index.html#index_refutable_slice)

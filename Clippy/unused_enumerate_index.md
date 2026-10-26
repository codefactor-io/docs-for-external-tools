Pattern: Unused `enumerate()` index

Issue: -

## Description

The index from `.enumerate()` is immediately dropped.

## What it does

Checks for uses of the `enumerate` method where the index is unused (`_`)

## Examples

Example of **incorrect** code:

```rust
let v = vec![1, 2, 3, 4];
for (_, x) in v.iter().enumerate() {
    println!("{x}");
}
```

Example of **correct** code:

```rust
let v = vec![1, 2, 3, 4];
for x in v.iter() {
    println!("{x}");
}
```

## Further Reading

* [Clippy - unused_enumerate_index](https://clippy.rust-lang.org/stable/index.html#unused_enumerate_index)

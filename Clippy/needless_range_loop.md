Pattern: Index-based loop over collection

Issue: -

## Description

Just iterating the collection itself makes the intent
more clear and is probably faster because it eliminates
the bounds check that is done when indexing.

## What it does

Checks for looping over the range of `0..len` of some
collection just to get the values by index.

## Examples

Example of **incorrect** code:

```rust
let vec = vec!['a', 'b', 'c'];
for i in 0..vec.len() {
    println!("{}", vec[i]);
}
```

Example of **correct** code:

```rust
let vec = vec!['a', 'b', 'c'];
for i in vec {
    println!("{}", i);
}
```

## Further Reading

* [Clippy - needless_range_loop](https://clippy.rust-lang.org/stable/index.html#needless_range_loop)

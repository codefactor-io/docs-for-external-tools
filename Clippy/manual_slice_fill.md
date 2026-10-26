Pattern: Missing use of `fill()` on slice

Issue: -

## Description

Using the `fill` method is more idiomatic and concise.

## What it does

Checks for manually filling a slice with a value.

## Examples

Example of **incorrect** code:

```rust
let mut some_slice = [1, 2, 3, 4, 5];
for i in 0..some_slice.len() {
    some_slice[i] = 0;
}
```

Example of **correct** code:

```rust
let mut some_slice = [1, 2, 3, 4, 5];
some_slice.fill(0);
```

## Further Reading

* [Clippy - manual_slice_fill](https://clippy.rust-lang.org/stable/index.html#manual_slice_fill)

Pattern: `Vec` or array with single range

Issue: -

## Description

This is almost always incorrect, as it will result in a `Vec` that has only one element.
Almost always, the programmer intended for it to include all elements in the range or for
the end of the range to be the length instead.

## What it does

Checks for `Vec` or array initializations that contain only one range.

## Examples

Example of **incorrect** code:

```rust
let x = [0..200];
```

Example of **correct** code:

```rust
// If it was intended to include every element in the range...
let x = (0..200).collect::<Vec<i32>>();
// ...Or if 200 was meant to be the len
let x = [0; 200];
```

## Further Reading

* [Clippy - single_range_in_vec_init](https://clippy.rust-lang.org/stable/index.html#single_range_in_vec_init)

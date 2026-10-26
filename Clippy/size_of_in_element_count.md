Pattern: `size_of::<T>()` used as element count

Issue: -

## Description

These functions expect a count
of `T` and not a number of bytes

## What it does

Detects expressions where
`size_of::<T>` or `size_of_val::<T>` is used as a
count of elements of type `T`

## Examples

Example of **incorrect** code:

```rust
const SIZE: usize = 128;
let x = [2u8; SIZE];
let mut y = [2u8; SIZE];
unsafe { copy_nonoverlapping(x.as_ptr(), y.as_mut_ptr(), size_of::<u8>() * SIZE) };
```

## Further Reading

* [Clippy - size_of_in_element_count](https://clippy.rust-lang.org/stable/index.html#size_of_in_element_count)

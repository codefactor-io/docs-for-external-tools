Pattern: Missing use of `size_of_val()`

Issue: -

## Description

* Shorter to write
* Removes the need for the human and the compiler to worry about overflow in the
  multiplication
* Potentially faster at runtime as rust emits special no-wrapping flags when it
  calculates the byte length
* Less turbofishing

## What it does

When `a` is `&[T]`, detect `a.len() * size_of::<T>()` and suggest `size_of_val(a)`
instead.

## Examples

Example of **incorrect** code:

```rust
let newlen = data.len() * size_of::<i32>();
```

Example of **correct** code:

```rust
let newlen = size_of_val(data);
```

## Further Reading

* [Clippy - manual_slice_size_calculation](https://clippy.rust-lang.org/stable/index.html#manual_slice_size_calculation)

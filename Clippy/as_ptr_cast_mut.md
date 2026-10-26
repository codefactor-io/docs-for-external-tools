Pattern: Cast of `as_ptr()` result to mutable pointer

Issue: -

## Description

Since `as_ptr` takes a `&self`, the pointer won't have write permissions unless interior
mutability is used, making it unlikely that having it as a mutable pointer is correct.

## What it does

Checks for the result of a `&self`-taking `as_ptr` being cast to a mutable pointer.

## Examples

Example of **incorrect** code:

```rust
let mut vec = Vec::<u8>::with_capacity(1);
let ptr = vec.as_ptr() as *mut u8;
unsafe { ptr.write(4) }; // UNDEFINED BEHAVIOUR
```

Example of **correct** code:

```rust
let mut vec = Vec::<u8>::with_capacity(1);
let ptr = vec.as_mut_ptr();
unsafe { ptr.write(4) };
```

## Further Reading

* [Clippy - as_ptr_cast_mut](https://clippy.rust-lang.org/stable/index.html#as_ptr_cast_mut)

Pattern: Missing use of `ptr::eq()`

Issue: -

## Description

`ptr::eq` can be used to compare `&T` references
(which coerce to `*const T` implicitly) by their address rather than
comparing the values they point to.

## What it does

Use `std::ptr::eq` when applicable

## Examples

Example of **incorrect** code:

```rust
let a = &[1, 2, 3];
let b = &[1, 2, 3];

assert!(a as *const _ as usize == b as *const _ as usize);
```

Example of **correct** code:

```rust
let a = &[1, 2, 3];
let b = &[1, 2, 3];

assert!(std::ptr::eq(a, b));
```

## Further Reading

* [Clippy - ptr_eq](https://clippy.rust-lang.org/stable/index.html#ptr_eq)

Pattern: Missing use of `&raw const` or `&raw mut`

Issue: -

## Description

This would improve readability and avoid creating a reference
that points to an uninitialized value or unaligned place.
Read the `&raw` explanation in the Reference for more information.

## What it does

Checks for the usage of `&expr as *const T` or
`&mut expr as *mut T`, and suggest using `&raw const` or
`&raw mut` instead.

## Examples

Example of **incorrect** code:

```rust
let val = 1;
let p = &val as *const i32;

let mut val_mut = 1;
let p_mut = &mut val_mut as *mut i32;
```

Example of **correct** code:

```rust
let val = 1;
let p = &raw const val;

let mut val_mut = 1;
let p_mut = &raw mut val_mut;
```

## Further Reading

* [Clippy - borrow_as_ptr](https://clippy.rust-lang.org/stable/index.html#borrow_as_ptr)

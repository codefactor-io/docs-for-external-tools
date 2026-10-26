Pattern: Use of `as` to cast reference to pointer

Issue: -

## Description

Using `as` casts may result in silently changing mutability or type.

## What it does

Checks for casts of references to pointer using `as`
and suggests `std::ptr::from_ref` and `std::ptr::from_mut` instead.

## Examples

Example of **incorrect** code:

```rust
let a_ref = &1;
let a_ptr = a_ref as *const _;
```

Example of **correct** code:

```rust
let a_ref = &1;
let a_ptr = std::ptr::from_ref(a_ref);
```

## Further Reading

* [Clippy - ref_as_ptr](https://clippy.rust-lang.org/stable/index.html#ref_as_ptr)

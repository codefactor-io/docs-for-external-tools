Pattern: Missing use of `ptr::dangling()`

Issue: -

## Description

This creates a dangling pointer and is better expressed as
{`std`, `core`}`::ptr::`{`dangling`, `dangling_mut`}.

## What it does

Checks for casts of small constant literals or `mem::align_of` results to raw pointers.

## Examples

Example of **incorrect** code:

```rust
let ptr = 4 as *const u32;
let aligned = std::mem::align_of::<u32>() as *const u32;
let mut_ptr: *mut i64 = 8 as *mut _;
```

Example of **correct** code:

```rust
let ptr = std::ptr::dangling::<u32>();
let aligned = std::ptr::dangling::<u32>();
let mut_ptr: *mut i64 = std::ptr::dangling_mut();
```

## Further Reading

* [Clippy - manual_dangling_ptr](https://clippy.rust-lang.org/stable/index.html#manual_dangling_ptr)

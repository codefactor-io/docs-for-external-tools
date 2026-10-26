Pattern: Use of `as` cast between raw pointers

Issue: -

## Description

Though `as` casts between raw pointers are not terrible,
`pointer::cast` is safer because it cannot accidentally change the
pointer's mutability, nor cast the pointer to other types like `usize`.

## What it does

Checks for `as` casts between raw pointers that don't change their
constness, namely `*const T` to `*const U` and `*mut T` to `*mut U`.

## Examples

Example of **incorrect** code:

```rust
let ptr: *const u32 = &42_u32;
let mut_ptr: *mut u32 = &mut 42_u32;
let _ = ptr as *const i32;
let _ = mut_ptr as *mut i32;
```

Example of **correct** code:

```rust
let ptr: *const u32 = &42_u32;
let mut_ptr: *mut u32 = &mut 42_u32;
let _ = ptr.cast::<i32>();
let _ = mut_ptr.cast::<i32>();
```

## Further Reading

* [Clippy - ptr_as_ptr](https://clippy.rust-lang.org/stable/index.html#ptr_as_ptr)

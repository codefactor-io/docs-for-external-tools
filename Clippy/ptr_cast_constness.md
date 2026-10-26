Pattern: Use of `as` to change pointer constness

Issue: -

## Description

Though `as` casts between raw pointers are not terrible, `pointer::cast_mut` and
`pointer::cast_const` are safer because they cannot accidentally cast the pointer to another
type. Or, when null pointers are involved, `null()` and `null_mut()` can be used directly.

## What it does

Checks for `as` casts between raw pointers that change their constness, namely `*const T` to
`*mut T` and `*mut T` to `*const T`.

## Examples

Example of **incorrect** code:

```rust
let ptr: *const u32 = &42_u32;
let mut_ptr = ptr as *mut u32;
let ptr = mut_ptr as *const u32;
let ptr1 = std::ptr::null::<u32>() as *mut u32;
let ptr2 = std::ptr::null_mut::<u32>() as *const u32;
let ptr3 = std::ptr::null::<u32>().cast_mut();
let ptr4 = std::ptr::null_mut::<u32>().cast_const();
```

Example of **correct** code:

```rust
let ptr: *const u32 = &42_u32;
let mut_ptr = ptr.cast_mut();
let ptr = mut_ptr.cast_const();
let ptr1 = std::ptr::null_mut::<u32>();
let ptr2 = std::ptr::null::<u32>();
let ptr3 = std::ptr::null_mut::<u32>();
let ptr4 = std::ptr::null::<u32>();
```

## Further Reading

* [Clippy - ptr_cast_constness](https://clippy.rust-lang.org/stable/index.html#ptr_cast_constness)

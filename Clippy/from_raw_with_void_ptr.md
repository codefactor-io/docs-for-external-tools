Pattern: Void pointer passed to `from_raw()`

Issue: -

## Description

When dealing with `c_void` raw pointers in FFI, it is easy to run into the pitfall of calling `from_raw` with the `c_void` pointer.
The type signature of `Box::from_raw` is `fn from_raw(raw: *mut T) -> Box<T>`, so if you pass a `*mut c_void` you will get a `Box<c_void>` (and similarly for `Rc`, `Arc` and `Weak`).
For this to be safe, `c_void` would need to have the same memory layout as the original type, which is often not the case.

## What it does

Checks if we're passing a `c_void` raw pointer to `{Box,Rc,Arc,Weak}::from_raw(_)`

## Examples

Example of **incorrect** code:

```rust
let ptr = Box::into_raw(Box::new(42usize)) as *mut c_void;
let _ = unsafe { Box::from_raw(ptr) };
```

Example of **correct** code:

```rust
let _ = unsafe { Box::from_raw(ptr as *mut usize) };
```

## Further Reading

* [Clippy - from_raw_with_void_ptr](https://clippy.rust-lang.org/stable/index.html#from_raw_with_void_ptr)

Pattern: Transmute between pointers or references

Issue: -

## Description

Transmutes are dangerous, and these can instead be
written as casts.

## What it does

Checks for transmutes from a pointer to a pointer, or
from a reference to a reference.

## Examples

```rust
let ptr = &1u32 as *const u32;
unsafe {
    // pointer-to-pointer transmute
    let _: *const f32 = std::mem::transmute(ptr);
    // ref-ref transmute
    let _: &f32 = std::mem::transmute(&1u32);
}
// These can be respectively written:
let _ = ptr as *const f32;
let _ = unsafe{ &*(&1u32 as *const u32 as *const f32) };
```

## Further Reading

* [Clippy - transmute_ptr_to_ptr](https://clippy.rust-lang.org/stable/index.html#transmute_ptr_to_ptr)

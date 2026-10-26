Pattern: `NonNull::new_unchecked()` on `Box` pointer

Issue: -

## Description

`NonNull::new_unchecked` is an unsafe function, which we don't need to call at all if we can instead use a mutable reference.

## What it does

Checks for unsafe usage of `NonNull::new_unchecked(Box::into_raw(x))`, and suggests calling `NonNull::from_mut(Box::leak(x))` instead.

## Examples

Example of **incorrect** code:

```rust
use std::ptr::NonNull;
let one = Box::new(1);
let ptr = unsafe { NonNull::new_unchecked(Box::into_raw(one)) };
```

Example of **correct** code:

```rust
use std::ptr::NonNull;
let one = Box::new(1);
let ptr = NonNull::from_mut(Box::leak(one));
```

## Further Reading

* [Clippy - nonnull_unchecked_on_box_ptr](https://clippy.rust-lang.org/stable/index.html#nonnull_unchecked_on_box_ptr)

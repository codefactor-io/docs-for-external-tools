Pattern: `mem::swap()` on pointer-derived references

Issue: -

## Description

When at least one parameter to `swap` is derived from a pointer it may overlap with the
other. This would then lead to undefined behavior.

## What it does

Checks for calls to `core::mem::swap` where either parameter is derived from a pointer

## Examples

Example of **incorrect** code:

```rust
unsafe fn swap(x: &[*mut u32], y: &[*mut u32]) {
    for (&x, &y) in x.iter().zip(y) {
        core::mem::swap(&mut *x, &mut *y);
    }
}
```

Example of **correct** code:

```rust
unsafe fn swap(x: &[*mut u32], y: &[*mut u32]) {
    for (&x, &y) in x.iter().zip(y) {
        core::ptr::swap(x, y);
    }
}
```

## Further Reading

* [Clippy - swap_ptr_to_ref](https://clippy.rust-lang.org/stable/index.html#swap_ptr_to_ref)

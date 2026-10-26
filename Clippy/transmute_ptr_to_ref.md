Pattern: Transmute from pointer to reference

Issue: -

## Description

This can always be rewritten with `&` and `*`.

## What it does

Checks for transmutes from a pointer to a reference.

## Examples

```rust
unsafe {
    let _: &T = std::mem::transmute(p); // where p: *const T
}

// can be written:
let _: &T = &*p;
```

## Known problems

- `mem::transmute` in statics and constants is stable from Rust 1.46.0,
while dereferencing raw pointer is not stable yet.
If you need to do this in those places,
you would have to use `transmute` instead.

## Further Reading

* [Clippy - transmute_ptr_to_ref](https://clippy.rust-lang.org/stable/index.html#transmute_ptr_to_ref)

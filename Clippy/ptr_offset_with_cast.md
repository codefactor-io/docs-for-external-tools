Pattern: Use of `offset()` with `usize` cast

Issue: -

## Description

If we’re always increasing the pointer address, we can avoid the numeric
cast by using the `add` method instead.

## What it does

Checks for usage of the `offset` pointer method with a `usize` cast to an
`isize`.

## Examples

Example of **incorrect** code:

```rust
let vec = vec![b'a', b'b', b'c'];
let ptr = vec.as_ptr();
let offset = 1_usize;

unsafe {
    ptr.offset(offset as isize);
}
```

Example of **correct** code:

```rust
let vec = vec![b'a', b'b', b'c'];
let ptr = vec.as_ptr();
let offset = 1_usize;

unsafe {
    ptr.add(offset);
}
```

## Further Reading

* [Clippy - ptr_offset_with_cast](https://clippy.rust-lang.org/stable/index.html#ptr_offset_with_cast)

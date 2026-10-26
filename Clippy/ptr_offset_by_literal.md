Pattern: Use of `offset()` with integer literal

Issue: -

## Description

The `add` and `sub` methods more accurately express the intent.

## What it does

Checks for usage of the `offset` pointer method with an integer
literal.

## Examples

Example of **incorrect** code:

```rust
let vec = vec![b'a', b'b', b'c'];
let ptr = vec.as_ptr();

unsafe {
    ptr.offset(-8);
}
```

Example of **correct** code:

```rust
let vec = vec![b'a', b'b', b'c'];
let ptr = vec.as_ptr();

unsafe {
    ptr.sub(8);
}
```

## Further Reading

* [Clippy - ptr_offset_by_literal](https://clippy.rust-lang.org/stable/index.html#ptr_offset_by_literal)

Pattern: Trailing zero-sized array without `repr`

Issue: -

## Description

Zero-sized arrays aren't very useful in Rust itself, so such a struct is likely being created to pass to C code or in some other situation where control over memory layout matters (for example, in conjunction with manual allocation to make it easy to compute the offset of the array). Either way, `#[repr(C)]` (or another `repr` attribute) is needed.

## What it does

Displays a warning when a struct with a trailing zero-sized array is declared without a `repr` attribute.

## Examples

Example of **incorrect** code:

```rust
struct RarelyUseful {
    some_field: u32,
    last: [u32; 0],
}
```

Example of **correct** code:

```rust
#[repr(C)]
struct MoreOftenUseful {
    some_field: usize,
    last: [u32; 0],
}
```

## Further Reading

* [Clippy - trailing_empty_array](https://clippy.rust-lang.org/stable/index.html#trailing_empty_array)

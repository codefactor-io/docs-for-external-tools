Pattern: Multiple unsafe operations in `unsafe` block

Issue: -

## Description

Combined with `undocumented_unsafe_blocks`,
this lint ensures that each unsafe operation must be independently justified.
Combined with `unused_unsafe`, this lint also ensures
elimination of unnecessary unsafe blocks through refactoring.

## What it does

Checks for `unsafe` blocks that contain more than one unsafe operation.

## Examples

Example of **incorrect** code:

```rust
/// Reads a `char` from the given pointer.
///
/// # Safety
///
/// `ptr` must point to four consecutive, initialized bytes which
/// form a valid `char` when interpreted in the native byte order.
fn read_char(ptr: *const u8) -> char {
    // SAFETY: The caller has guaranteed that the value pointed
    // to by `bytes` is a valid `char`.
    unsafe { char::from_u32_unchecked(*ptr.cast::<u32>()) }
}
```

Example of **correct** code:

```rust
/// Reads a `char` from the given pointer.
///
/// # Safety
///
/// - `ptr` must be 4-byte aligned, point to four consecutive
///   initialized bytes, and be valid for reads of 4 bytes.
/// - The bytes pointed to by `ptr` must represent a valid
///   `char` when interpreted in the native byte order.
fn read_char(ptr: *const u8) -> char {
    // SAFETY: `ptr` is 4-byte aligned, points to four consecutive
    // initialized bytes, and is valid for reads of 4 bytes.
    let int_value = unsafe { *ptr.cast::<u32>() };

    // SAFETY: The caller has guaranteed that the four bytes
    // pointed to by `bytes` represent a valid `char`.
    unsafe { char::from_u32_unchecked(int_value) }
}
```

## Notes

- Unsafe operations only count towards the total for the innermost
  enclosing `unsafe` block.
- Each call to a macro expanding to unsafe operations count for one
  unsafe operation.
- Taking a raw pointer to a union field is always safe and will
  not be considered unsafe by this lint, even when linting code written
  with a specified Rust version of 1.91 or earlier (which required
  using an `unsafe` block).

## Further Reading

* [Clippy - multiple_unsafe_ops_per_block](https://clippy.rust-lang.org/stable/index.html#multiple_unsafe_ops_per_block)

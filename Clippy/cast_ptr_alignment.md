Pattern: Cast to more strictly aligned pointer

Issue: -

## Description

Dereferencing the resulting pointer may be undefined behavior.

## What it does

Checks for casts, using `as` or `pointer::cast`, from a
less strictly aligned pointer to a more strictly aligned pointer.

## Examples

Example of **incorrect** code:

```rust
let _ = (&1u8 as *const u8) as *const u16;
let _ = (&mut 1u8 as *mut u8) as *mut u16;

(&1u8 as *const u8).cast::<u16>();
(&mut 1u8 as *mut u8).cast::<u16>();
```

## Known problems

Using [`std::ptr::read_unaligned`](https://doc.rust-lang.org/std/ptr/fn.read_unaligned.html) and [`std::ptr::write_unaligned`](https://doc.rust-lang.org/std/ptr/fn.write_unaligned.html) or
similar on the resulting pointer is fine. Is over-zealous: casts with
manual alignment checks or casts like `u64` -> `u8` -> `u16` can be
fine. Miri is able to do a more in-depth analysis.

## Further Reading

* [Clippy - cast_ptr_alignment](https://clippy.rust-lang.org/stable/index.html#cast_ptr_alignment)

Pattern: Use of `as` conversion

Issue: -

## Description

`as` conversions will perform many kinds of
conversions, including silently lossy conversions and dangerous coercions.
There are cases when it makes sense to use `as`, so the lint is
Allow by default.

## What it does

Checks for usage of `as` conversions.

Note that this lint is specialized in linting *every single* use of `as`
regardless of whether good alternatives exist or not. If you want more
precise lints for `as`, please consider using these separate lints:

- `clippy::cast_lossless`
- `clippy::cast_possible_truncation`
- `clippy::cast_possible_wrap`
- `clippy::cast_precision_loss`
- `clippy::cast_sign_loss`
- `clippy::char_lit_as_u8`
- `clippy::fn_to_numeric_cast`
- `clippy::fn_to_numeric_cast_with_truncation`
- `clippy::ptr_as_ptr`
- `clippy::unnecessary_cast`
- `invalid_reference_casting`

There is a good explanation the reason why this lint should work in this
way and how it is useful [in this
issue](https://github.com/rust-lang/rust-clippy/issues/5122).

## Examples

Example of **incorrect** code:

```rust
let a: u32;
...
f(a as u16);
```

Example of **correct** code:

```rust
f(a.try_into()?);

// or

f(a.try_into().expect("Unexpected u16 overflow in f"));
```

## Further Reading

* [Clippy - as_conversions](https://clippy.rust-lang.org/stable/index.html#as_conversions)

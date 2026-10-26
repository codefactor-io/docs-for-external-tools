Pattern: Function pointer cast to non-`usize` type

Issue: -

## Description

Casting a function pointer to anything other than `usize`/`isize` is
not portable across architectures. If the target type is too small the
address would be truncated, and target types larger than `usize` are
unnecessary.

Casting to `isize` also doesn't make sense, since addresses are never
signed.

## What it does

Checks for casts of function pointers to something other than `usize`.

## Examples

Example of **incorrect** code:

```rust
fn fun() -> i32 { 1 }
let _ = fun as i64;
```

Example of **correct** code:

```rust
let _ = fun as usize;
```

## Further Reading

* [Clippy - fn_to_numeric_cast](https://clippy.rust-lang.org/stable/index.html#fn_to_numeric_cast)

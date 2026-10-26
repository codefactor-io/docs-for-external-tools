Pattern: Missing use of `c""` literal

Issue: -

## Description

This can be written more concisely using `c"str"` literals and is also less error-prone,
because the compiler checks for interior `NUL` bytes and the terminating `NUL` byte is inserted automatically.

## What it does

Checks for the manual creation of C strings (a string with a `NUL` byte at the end), either
through one of the `CStr` constructor functions, or more plainly by calling `.as_ptr()`
on a (byte) string literal with a hardcoded `\0` byte at the end.

## Examples

Example of **incorrect** code:

```rust
fn needs_cstr(_: &CStr) {}

needs_cstr(CStr::from_bytes_with_nul(b"Hello\0").unwrap());
unsafe { libc::puts("World\0".as_ptr().cast()) }
```

Example of **correct** code:

```rust
fn needs_cstr(_: &CStr) {}

needs_cstr(c"Hello");
unsafe { libc::puts(c"World".as_ptr()) }
```

## Further Reading

* [Clippy - manual_c_str_literals](https://clippy.rust-lang.org/stable/index.html#manual_c_str_literals)

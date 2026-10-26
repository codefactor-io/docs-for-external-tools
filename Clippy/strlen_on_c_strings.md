Pattern: Use of `libc::strlen` on `CString` or `CStr`

Issue: -

## Description

libc::strlen is an unsafe function, which we don't need to call
if all we want to know is the length of the c-string.

## What it does

Checks for usage of `libc::strlen` on a `CString` or `CStr` value,
and suggest calling `count_bytes()` instead.

## Examples

Example of **incorrect** code:

```rust
use std::ffi::CString;
let cstring = CString::new("foo").expect("CString::new failed");
let len = unsafe { libc::strlen(cstring.as_ptr()) };
```

Example of **correct** code:

```rust
use std::ffi::CString;
let cstring = CString::new("foo").expect("CString::new failed");
let len = cstring.count_bytes();
```

## Further Reading

* [Clippy - strlen_on_c_strings](https://clippy.rust-lang.org/stable/index.html#strlen_on_c_strings)

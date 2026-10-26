Pattern: Raw pointer argument dereferenced in safe function

Issue: -

## Description

The function should almost definitely be marked `unsafe`, since for an
arbitrary raw pointer, there is no way of telling for sure if it is valid.

In general, this lint should **never be disabled** unless it is definitely a
false positive (please submit an issue if so) since it breaks Rust's
soundness guarantees, directly exposing API users to potentially dangerous
program behavior. This is also true for internal APIs, as it is easy to leak
unsoundness.

## What it does

Checks for public functions that dereference raw pointer
arguments but are not marked `unsafe`.

## Examples

Example of **incorrect** code:

```rust
pub fn foo(x: *const u8) {
    println!("{}", unsafe { *x });
}

// this call "looks" safe but will segfault or worse!
// foo(invalid_ptr);
```

Example of **correct** code:

```rust
pub unsafe fn foo(x: *const u8) {
    println!("{}", unsafe { *x });
}

// this would cause a compiler error for calling without `unsafe`
// foo(invalid_ptr);

// sound call if the caller knows the pointer is valid
unsafe { foo(valid_ptr); }
```

## Context

In Rust, an `unsafe {...}` block is used to indicate that the code in that
section has been verified in some way that the compiler can not. For a
function that accepts a raw pointer then accesses the pointer's data, this is
generally impossible as the incoming pointer could point anywhere, valid or
not. So, the signature should be marked `unsafe fn`: this indicates that the
function's caller must provide some verification that the arguments it sends
are valid (and then call the function within an `unsafe` block).

## Known problems

* It does not check functions recursively so if the pointer is passed to a
private non-`unsafe` function which does the dereferencing, the lint won't
trigger (false negative).
* It only checks for arguments whose type are raw pointers, not raw pointers
got from an argument in some other way (`fn foo(bar: &[*const u8])` or
`some_argument.get_raw_ptr()`) (false negative).

## Further Reading

* [Clippy - not_unsafe_ptr_arg_deref](https://clippy.rust-lang.org/stable/index.html#not_unsafe_ptr_arg_deref)

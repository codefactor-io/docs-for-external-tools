Pattern: Transmute of null to function pointer

Issue: -

## Description

Creating a null function pointer is undefined behavior.

More info: https://doc.rust-lang.org/nomicon/ffi.html#the-nullable-pointer-optimization

## What it does

Checks for null function pointer creation through transmute.

## Examples

Example of **incorrect** code:

```rust
let null_fn: fn() = unsafe { std::mem::transmute( std::ptr::null::<()>() ) };
```

Example of **correct** code:

```rust
let null_fn: Option<fn()> = None;
```

## Known problems

Not all cases can be detected at the moment of this writing.
For example, variables which hold a null pointer and are then fed to a `transmute`
call, aren't detectable yet.

## Further Reading

* [Clippy - transmute_null_to_fn](https://clippy.rust-lang.org/stable/index.html#transmute_null_to_fn)

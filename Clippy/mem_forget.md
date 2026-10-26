Pattern: Use of `mem::forget()` on `Drop` type

Issue: -

## Description

`std::mem::forget(t)` prevents `t` from running its destructor, possibly causing leaks.
It is not possible to detect all means of creating leaks, but it may be desirable to
prohibit the simple ones.

## What it does

Checks for usage of `std::mem::forget(t)` where `t` is
`Drop` or has a field that implements `Drop`.

## Examples

Example of **incorrect** code:

```rust
mem::forget(Rc::new(55))
```

## Further Reading

* [Clippy - mem_forget](https://clippy.rust-lang.org/stable/index.html#mem_forget)

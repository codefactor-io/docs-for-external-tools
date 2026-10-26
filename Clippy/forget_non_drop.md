Pattern: Use of `mem::forget()` on non-`Drop` value

Issue: -

## Description

Calling `std::mem::forget` is no different than dropping such a type. A different value may
have been intended.

## What it does

Checks for calls to `std::mem::forget` with a value that does not implement `Drop`.

## Examples

Example of **incorrect** code:

```rust
struct Foo;
let x = Foo;
std::mem::forget(x);
```

## Further Reading

* [Clippy - forget_non_drop](https://clippy.rust-lang.org/stable/index.html#forget_non_drop)

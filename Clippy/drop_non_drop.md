Pattern: Use of `mem::drop()` on non-`Drop` value

Issue: -

## Description

Calling `std::mem::drop` is no different than dropping such a type. A different value may
have been intended.

## What it does

Checks for calls to `std::mem::drop` with a value that does not implement `Drop`.

## Examples

Example of **incorrect** code:

```rust
struct Foo;
let x = Foo;
std::mem::drop(x);
```

## Further Reading

* [Clippy - drop_non_drop](https://clippy.rust-lang.org/stable/index.html#drop_non_drop)

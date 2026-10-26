Pattern: Use of `with_capacity(0)`

Issue: -

## Description

Calling `with_capacity(0)` does not allocate any initial capacity and behaves identically
to `new()`. Using `new()` is more idiomatic, concise, and is a `const fn` for these types.

## What it does

Checks for calls to `with_capacity(0)` on standard library collections and types.

## Examples

Example of **incorrect** code:

```rust
let v: Vec<i32> = Vec::with_capacity(0);
let s = String::with_capacity(0);
```

Example of **correct** code:

```rust
let v: Vec<i32> = Vec::new();
let s = String::new();
```

## Further Reading

* [Clippy - with_capacity_zero](https://clippy.rust-lang.org/stable/index.html#with_capacity_zero)

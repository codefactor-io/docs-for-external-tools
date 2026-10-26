Pattern: Cast of `0` to raw pointer

Issue: -

## Description

This generally means `null` and is better expressed as
{`std`, `core`}`::ptr::`{`null`, `null_mut`}.

## What it does

Catch casts from `0` to some pointer type

## Examples

Example of **incorrect** code:

```rust
let a = 0 as *const u32;
```

Example of **correct** code:

```rust
let a = std::ptr::null::<u32>();
```

## Further Reading

* [Clippy - zero_ptr](https://clippy.rust-lang.org/stable/index.html#zero_ptr)

Pattern: `#[no_mangle]` on function with Rust ABI

Issue: -

## Description

The Rust ABI is not stable, but in many simple cases matches
enough with the C ABI that it is possible to forget to add
`extern "C"` to a function called from C. Changes to the
Rust ABI can break this at any point.

## What it does

Checks for Rust ABI functions with the `#[no_mangle]` attribute.

## Examples

Example of **incorrect** code:

```rust
 #[no_mangle]
 fn example(arg_one: u32, arg_two: usize) {}
```

Example of **correct** code:

```rust
 #[no_mangle]
 extern "C" fn example(arg_one: u32, arg_two: usize) {}
```

## Further Reading

* [Clippy - no_mangle_with_rust_abi](https://clippy.rust-lang.org/stable/index.html#no_mangle_with_rust_abi)

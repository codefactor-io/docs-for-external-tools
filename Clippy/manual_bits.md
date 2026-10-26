Pattern: Missing use of `T::BITS`

Issue: -

## Description

Can be written as the shorter `T::BITS`.

## What it does

Checks for usage of `size_of::<T>() * 8` when
`T::BITS` is available.

## Examples

Example of **incorrect** code:

```rust
size_of::<usize>() * 8;
```

Example of **correct** code:

```rust
usize::BITS as usize;
```

## Further Reading

* [Clippy - manual_bits](https://clippy.rust-lang.org/stable/index.html#manual_bits)

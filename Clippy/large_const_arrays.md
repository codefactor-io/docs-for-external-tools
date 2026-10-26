Pattern: Large `const` array

Issue: -

## Description

Performance: const variables are inlined upon use.
Static items result in only one instance and has a fixed location in memory.

## What it does

Checks for large `const` arrays that should
be defined as `static` instead.

## Examples

Example of **incorrect** code:

```rust
pub const a = [0u32; 1_000_000];
```

Example of **correct** code:

```rust
pub static a = [0u32; 1_000_000];
```

## Further Reading

* [Clippy - large_const_arrays](https://clippy.rust-lang.org/stable/index.html#large_const_arrays)

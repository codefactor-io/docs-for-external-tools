Pattern: Large array on stack

Issue: -

## Description

Large local arrays may cause stack overflow.

## What it does

Checks for local arrays that may be too large.

## Examples

Example of **incorrect** code:

```rust
let a = [0u32; 1_000_000];
```

## Further Reading

* [Clippy - large_stack_arrays](https://clippy.rust-lang.org/stable/index.html#large_stack_arrays)

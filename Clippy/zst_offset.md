Pattern: Pointer offset on zero-sized type

Issue: -

## Description

This is a no-op, and likely unintended

## What it does

Checks for `offset(_)`, `wrapping_`{`add`, `sub`}, etc. on raw pointers to
zero-sized types

## Examples

Example of **incorrect** code:

```rust
unsafe { (&() as *const ()).offset(1) };
```

## Further Reading

* [Clippy - zst_offset](https://clippy.rust-lang.org/stable/index.html#zst_offset)

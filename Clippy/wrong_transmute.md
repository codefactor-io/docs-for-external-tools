Pattern: Invalid transmute

Issue: -

## Description

It's basically guaranteed to be undefined behavior.

## What it does

Checks for transmutes that can't ever be correct on any
architecture.

## Examples

Example of **incorrect** code:

```rust
let ptr: *const T = core::intrinsics::transmute('x')
```

## Known problems

When accessing C, users might want to store pointer
sized objects in `extradata` arguments to save an allocation.

## Further Reading

* [Clippy - wrong_transmute](https://clippy.rust-lang.org/stable/index.html#wrong_transmute)

Pattern: Use of underscore-prefixed binding

Issue: -

## Description

A single leading underscore is usually used to indicate
that a binding will not be used. Using such a binding breaks this
expectation.

## What it does

Checks for the use of bindings with a single leading
underscore.

## Examples

Example of **incorrect** code:

```rust
let _x = 0;
let y = _x + 1; // Here we are using `_x`, even though it has a leading
                // underscore. We should rename `_x` to `x`
```

## Known problems

The lint does not work properly with desugaring and
macro, it has been allowed in the meantime.

## Further Reading

* [Clippy - used_underscore_binding](https://clippy.rust-lang.org/stable/index.html#used_underscore_binding)

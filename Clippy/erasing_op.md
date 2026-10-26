Pattern: Erasing operation like `x * 0`

Issue: -

## Description

The whole expression can be replaced by zero.
This is most likely not the intended outcome and should probably be
corrected

## What it does

Checks for erasing operations, e.g., `x * 0`.

## Examples

Example of **incorrect** code:

```rust
let x = 1;
0 / x;
0 * x;
x & 0;
```

## Further Reading

* [Clippy - erasing_op](https://clippy.rust-lang.org/stable/index.html#erasing_op)

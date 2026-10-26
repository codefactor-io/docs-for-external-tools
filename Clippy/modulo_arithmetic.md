Pattern: Use of modulo arithmetic

Issue: -

## Description

The results of modulo (`%`) operation might differ
depending on the language, when negative numbers are involved.
If you interop with different languages it might be beneficial
to double check all places that use modulo arithmetic.

For example, in Rust `17 % -3 = 2`, but in Python `17 % -3 = -1`.

## What it does

Checks for modulo arithmetic.

## Examples

Example of **incorrect** code:

```rust
let x = -17 % 3;
```

## Further Reading

* [Clippy - modulo_arithmetic](https://clippy.rust-lang.org/stable/index.html#modulo_arithmetic)

Pattern: Loop that never repeats

Issue: -

## Description

This loop never loops, all it does is obfuscating the
code.

## What it does

Checks for loops that will always `break`, `return` or
`continue` an outer loop.

## Examples

Example of **incorrect** code:

```rust
loop {
    ..;
    break;
}
```

## Further Reading

* [Clippy - never_loop](https://clippy.rust-lang.org/stable/index.html#never_loop)

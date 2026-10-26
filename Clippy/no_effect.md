Pattern: Statement with no effect

Issue: -

## Description

Unlike dead code, these statements are actually
executed. However, as they have no effect, all they do is make the code less
readable.

## What it does

Checks for statements which have no effect.

## Examples

Example of **incorrect** code:

```rust
0;
```

## Further Reading

* [Clippy - no_effect](https://clippy.rust-lang.org/stable/index.html#no_effect)

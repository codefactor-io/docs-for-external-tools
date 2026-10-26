Pattern: Missing use of `rotate_left()`/`rotate_right()`

Issue: -

## Description

Calling the function better conveys the intent.

## What it does

It detects manual bit rotations that could be rewritten using standard
functions `rotate_left` or `rotate_right`.

## Examples

Example of **incorrect** code:

```rust
let x = 12345678_u32;
let _ = (x >> 8) | (x << 24);
```

Example of **correct** code:

```rust
let x = 12345678_u32;
let _ = x.rotate_right(8);
```

## Known issues

Currently, the lint only catches shifts by constant amount.

## Further Reading

* [Clippy - manual_rotate](https://clippy.rust-lang.org/stable/index.html#manual_rotate)

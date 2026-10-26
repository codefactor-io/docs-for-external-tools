Pattern: Missing use of `saturating_sub()`

Issue: -

## Description

Simplicity and readability. Instead we can easily use an builtin function.

## What it does

Checks for implicit saturating subtraction.

## Examples

Example of **incorrect** code:

```rust
let mut i: u32 = end - start;

if i != 0 {
    i -= 1;
}
```

Example of **correct** code:

```rust
let mut i: u32 = end - start;

i = i.saturating_sub(1);
```

## Further Reading

* [Clippy - implicit_saturating_sub](https://clippy.rust-lang.org/stable/index.html#implicit_saturating_sub)

Pattern: Inverted subtraction after comparison

Issue: -

## Description

This could result in an underflow and is most likely not what the user wants. If this was
intended to be a saturated subtraction, consider using the `saturating_sub` method directly.

## What it does

Checks for comparisons between integers, followed by subtracting the greater value from the
lower one.

## Examples

Example of **incorrect** code:

```rust
let a = 12u32;
let b = 13u32;

let result = if a > b { b - a } else { 0 };
```

Example of **correct** code:

```rust
let a = 12u32;
let b = 13u32;

let result = a.saturating_sub(b);
```

## Further Reading

* [Clippy - inverted_saturating_sub](https://clippy.rust-lang.org/stable/index.html#inverted_saturating_sub)

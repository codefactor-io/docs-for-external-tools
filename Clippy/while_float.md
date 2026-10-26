Pattern: Floating-point comparison in `while` loop

Issue: -

## Description

If you increment floating point values, errors can compound,
so, use integers instead if possible.

## What it does

Checks for while loops comparing floating point values.

## Examples

Example of **incorrect** code:

```rust
let mut x = 0.0;
while x < 42.0 {
    x += 1.0;
}
```

Example of **correct** code:

```rust
let mut x = 0;
while x < 42 {
    x += 1;
}
```

## Known problems

The lint will catch all while loops comparing floating point
values without regarding the increment.

## Further Reading

* [Clippy - while_float](https://clippy.rust-lang.org/stable/index.html#while_float)

Pattern: Missing use of `is_power_of_two()`

Issue: -

## Description

Manual reimplementations of `is_power_of_two` increase code complexity for little benefit.

## What it does

Checks for expressions like `x.count_ones() == 1` or `x & (x - 1) == 0`, with x and unsigned integer, which may be manual
reimplementations of `x.is_power_of_two()`.

## Examples

Example of **incorrect** code:

```rust
let a: u32 = 4;
let result = a.count_ones() == 1;
```

Example of **correct** code:

```rust
let a: u32 = 4;
let result = a.is_power_of_two();
```

## Further Reading

* [Clippy - manual_is_power_of_two](https://clippy.rust-lang.org/stable/index.html#manual_is_power_of_two)

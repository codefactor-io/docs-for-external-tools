Pattern: OR pattern instead of range pattern

Issue: -

## Description

Using an explicit range is more concise and easier to read.

## What it does

Looks for combined OR patterns that are all contained in a specific range,
e.g. `6 | 4 | 5 | 9 | 7 | 8` can be rewritten as `4..=9`.

## Examples

Example of **incorrect** code:

```rust
let x = 6;
let foo = matches!(x, 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10);
```

Example of **correct** code:

```rust
let x = 6;
let foo = matches!(x, 1..=10);
```

## Known issues

This lint intentionally does not handle numbers greater than `i128::MAX` for `u128` literals
in order to support negative numbers.

## Further Reading

* [Clippy - manual_range_patterns](https://clippy.rust-lang.org/stable/index.html#manual_range_patterns)

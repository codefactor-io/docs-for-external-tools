Pattern: Comparison with boolean in `assert_eq!`

Issue: -

## Description

It is shorter to use the equivalent.

## What it does

This lint warns about boolean comparisons in assert-like macros.

## Examples

Example of **incorrect** code:

```rust
assert_eq!("a".is_empty(), false);
assert_ne!("a".is_empty(), true);
```

Example of **correct** code:

```rust
assert!(!"a".is_empty());
```

## Further Reading

* [Clippy - bool_assert_comparison](https://clippy.rust-lang.org/stable/index.html#bool_assert_comparison)

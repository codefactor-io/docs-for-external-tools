Pattern: Missing use of `assert_eq!`

Issue: -

## Description

`assert_{eq,ne}!` and `debug_assert_{eq,ne}!` achieves the same goal, and provides some
additional debug information

## What it does

Checks for `assert!` and `debug_assert!` that consist of only an (in)equality check

## Examples

Example of **incorrect** code:

```rust
assert!(2 * 2 == 4);
assert!(2 * 2 != 5);
debug_assert!(2 * 2 == 4);
debug_assert!(2 * 2 != 5);
```

Example of **correct** code:

```rust
assert_eq!(2 * 2, 4);
assert_ne!(2 * 2, 5);
debug_assert_eq!(2 * 2, 4);
debug_assert_ne!(2 * 2, 5);
```

## Further Reading

* [Clippy - manual_assert_eq](https://clippy.rust-lang.org/stable/index.html#manual_assert_eq)

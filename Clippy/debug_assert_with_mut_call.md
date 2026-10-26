Pattern: Mutating call in `debug_assert!`

Issue: -

## Description

In release builds `debug_assert!` macros are optimized out by the
compiler.
Therefore mutating something in a `debug_assert!` macro results in different behavior
between a release and debug build.

## What it does

Checks for function/method calls with a mutable
parameter in `debug_assert!`, `debug_assert_eq!` and `debug_assert_ne!` macros.

## Examples

Example of **incorrect** code:

```rust
debug_assert_eq!(vec![3].pop(), Some(3));

// or

debug_assert!(takes_a_mut_parameter(&mut x));
```

## Further Reading

* [Clippy - debug_assert_with_mut_call](https://clippy.rust-lang.org/stable/index.html#debug_assert_with_mut_call)

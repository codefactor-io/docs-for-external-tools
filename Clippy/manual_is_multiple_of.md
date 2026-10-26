Pattern: Missing use of `is_multiple_of()`

Issue: -

## Description

`a.is_multiple_of(b)` is a clearer way to check for divisibility
of `a` by `b`. This expression can never panic.

## What it does

Checks for manual implementation of `.is_multiple_of()` on
unsigned integer types.

## Examples

Example of **incorrect** code:

```rust
if a % b == 0 {
    println!("{a} is divisible by {b}");
}
```

Example of **correct** code:

```rust
if a.is_multiple_of(b) {
    println!("{a} is divisible by {b}");
}
```

## Further Reading

* [Clippy - manual_is_multiple_of](https://clippy.rust-lang.org/stable/index.html#manual_is_multiple_of)

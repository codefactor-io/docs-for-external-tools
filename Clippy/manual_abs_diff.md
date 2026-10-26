Pattern: Missing use of `abs_diff()`

Issue: -

## Description

Using `abs_diff` is shorter, more readable, and avoids control flow.

## What it does

Detects patterns like `if a > b { a - b } else { b - a }` and suggests using `a.abs_diff(b)`.

## Examples

Example of **incorrect** code:

```rust
if a > b {
    a - b
} else {
    b - a
}
```

Example of **correct** code:

```rust
a.abs_diff(b)
```

## Further Reading

* [Clippy - manual_abs_diff](https://clippy.rust-lang.org/stable/index.html#manual_abs_diff)

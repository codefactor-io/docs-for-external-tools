Pattern: Missing final `else` after `else if`

Issue: -

## Description

Some coding guidelines require this (e.g., MISRA-C:2004 Rule 14.10).

## What it does

Checks for usage of if expressions with an `else if` branch,
but without a final `else` branch.

## Examples

Example of **incorrect** code:

```rust
if x.is_positive() {
    a();
} else if x.is_negative() {
    b();
}
```

Example of **correct** code:

```rust
if x.is_positive() {
    a();
} else if x.is_negative() {
    b();
} else {
    // We don't care about zero.
}
```

## Further Reading

* [Clippy - else_if_without_else](https://clippy.rust-lang.org/stable/index.html#else_if_without_else)

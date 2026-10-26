Pattern: Missing use of `saturating_add()`

Issue: -

## Description

The built-in function is more readable and may be faster.

## What it does

Checks for implicit saturating addition.

## Examples

Example of **incorrect** code:

```rust
let mut u:u32 = 7000;

if u != u32::MAX {
    u += 1;
}
```

Example of **correct** code:

```rust
let mut u:u32 = 7000;

u = u.saturating_add(1);
```

## Further Reading

* [Clippy - implicit_saturating_add](https://clippy.rust-lang.org/stable/index.html#implicit_saturating_add)

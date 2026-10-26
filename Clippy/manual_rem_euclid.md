Pattern: Missing use of `rem_euclid()`

Issue: -

## Description

It's simpler and more readable.

## What it does

Checks for an expression like `((x % 4) + 4) % 4` which is a common manual reimplementation
of `x.rem_euclid(4)`.

## Examples

Example of **incorrect** code:

```rust
let x: i32 = 24;
let rem = ((x % 4) + 4) % 4;
```

Example of **correct** code:

```rust
let x: i32 = 24;
let rem = x.rem_euclid(4);
```

## Further Reading

* [Clippy - manual_rem_euclid](https://clippy.rust-lang.org/stable/index.html#manual_rem_euclid)

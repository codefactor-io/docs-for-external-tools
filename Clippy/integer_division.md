Pattern: Integer division

Issue: -

## Description

When outside of some very specific algorithms,
integer division is very often a mistake because it discards the
remainder.

## What it does

Checks for division of integers

## Examples

Example of **incorrect** code:

```rust
let x = 3 / 2;
println!("{}", x);
```

Example of **correct** code:

```rust
let x = 3f32 / 2f32;
println!("{}", x);
```

## Further Reading

* [Clippy - integer_division](https://clippy.rust-lang.org/stable/index.html#integer_division)

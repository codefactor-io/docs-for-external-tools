Pattern: Use of `/` or `%` on integers

Issue: -

## Description

In cryptographic contexts, division can result in timing sidechannel vulnerabilities,
and needs to be replaced with constant-time code instead (e.g. Barrett reduction).

## What it does

Checks for the usage of division (`/`) and remainder (`%`) operations
when performed on any integer types using the default `Div` and `Rem` trait implementations.

## Examples

Example of **incorrect** code:

```rust
let my_div = 10 / 2;
```

Example of **correct** code:

```rust
let my_div = 10 >> 1;
```

## Further Reading

* [Clippy - integer_division_remainder_used](https://clippy.rust-lang.org/stable/index.html#integer_division_remainder_used)

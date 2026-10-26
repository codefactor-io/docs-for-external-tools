Pattern: Name of only underscores and digits

Issue: -

## Description

It's hard to memorize what a variable means without a
descriptive name.

## What it does

Checks if you have variables whose name consists of just
underscores and digits.

## Examples

Example of **incorrect** code:

```rust
let _1 = 1;
let ___1 = 1;
let __1___2 = 11;
```

## Further Reading

* [Clippy - just_underscores_and_digits](https://clippy.rust-lang.org/stable/index.html#just_underscores_and_digits)

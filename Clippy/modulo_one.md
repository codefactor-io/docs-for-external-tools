Pattern: Integer modulo by one

Issue: -

## Description

The result for a divisor of one can only ever be zero; for
minus one it can cause panic/overflow (if the left operand is the minimal value of
the respective integer type) or results in zero. No one will write such code
deliberately, unless trying to win an Underhanded Rust Contest. Even for that
contest, it's probably a bad idea. Use something more underhanded.

## What it does

Checks for getting the remainder of integer division by one or minus
one.

## Examples

Example of **incorrect** code:

```rust
let a = x % 1;
let a = x % -1;
```

## Further Reading

* [Clippy - modulo_one](https://clippy.rust-lang.org/stable/index.html#modulo_one)

Pattern: Multiplication by `-1`

Issue: -

## Description

It's more readable to just negate.

## What it does

Checks for multiplication by -1 as a form of negation.

## Examples

Example of **incorrect** code:

```rust
let a = x * -1;
```

Example of **correct** code:

```rust
let a = -x;
```

## Further Reading

* [Clippy - neg_multiply](https://clippy.rust-lang.org/stable/index.html#neg_multiply)

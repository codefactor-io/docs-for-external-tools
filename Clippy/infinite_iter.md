Pattern: Infinite iteration

Issue: -

## Description

While there may be places where this is acceptable
(e.g., in event streams), in most cases this is simply an error.

## What it does

Checks for iteration that is guaranteed to be infinite.

## Examples

Example of **incorrect** code:

```rust
use std::iter;

iter::repeat(1_u8).collect::<Vec<_>>();
```

## Further Reading

* [Clippy - infinite_iter](https://clippy.rust-lang.org/stable/index.html#infinite_iter)

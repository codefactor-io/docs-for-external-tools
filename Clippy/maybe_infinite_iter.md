Pattern: Possible infinite iteration

Issue: -

## Description

While there may be places where this is acceptable
(e.g., in event streams), in most cases this is simply an error.

## What it does

Checks for iteration that may be infinite.

## Examples

Example of **incorrect** code:

```rust
let infinite_iter = 0..;
[0..].iter().zip(infinite_iter.take_while(|x| *x > 5));
```

## Known problems

The code may have a condition to stop iteration, but
this lint is not clever enough to analyze it.

## Further Reading

* [Clippy - maybe_infinite_iter](https://clippy.rust-lang.org/stable/index.html#maybe_infinite_iter)

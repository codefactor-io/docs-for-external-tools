Pattern: Bitwise operator on booleans

Issue: -

## Description

The bitwise operators do not support short-circuiting, so it may hinder code performance.
Additionally, boolean logic "masked" as bitwise logic is not caught by lints like `unnecessary_fold`

## What it does

Checks for usage of bitwise and/or operators between booleans, where performance may be improved by using
a lazy and.

## Examples

Example of **incorrect** code:

```rust
let (x,y) = (true, false);
if x & !y {} // where both x and y are booleans
```

Example of **correct** code:

```rust
let (x,y) = (true, false);
if x && !y {}
```

## Known problems

This lint evaluates only when the right side is determined to have no side effects. At this time, that
determination is quite conservative.

## Further Reading

* [Clippy - needless_bitwise_bool](https://clippy.rust-lang.org/stable/index.html#needless_bitwise_bool)

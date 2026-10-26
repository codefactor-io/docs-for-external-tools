Pattern: Comparison with boolean literal

Issue: -

## Description

Unnecessary code.

## What it does

Checks for expressions of the form `x == true`,
`x != true` and order comparisons such as `x < true` (or vice versa) and
suggest using the variable directly.

## Examples

```rust
if x == true {}
if y == false {}
```
use `x` directly:
```rust
if x {}
if !y {}
```

## Further Reading

* [Clippy - bool_comparison](https://clippy.rust-lang.org/stable/index.html#bool_comparison)

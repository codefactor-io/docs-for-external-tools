Pattern: Inclusive range with upper bound minus one

Issue: -

## Description

The code is more readable with an exclusive range
like `x..y`.

## What it does

Checks for inclusive ranges where 1 is subtracted from
the upper bound, e.g., `x..=(y-1)`.

## Examples

Example of **incorrect** code:

```rust
for i in x..=(y-1) {
    // ..
}
```

Example of **correct** code:

```rust
for i in x..y {
    // ..
}
```

## Limitations

The lint is conservative and will trigger only when switching
from an inclusive to an exclusive range is provably safe from
a typing point of view. This corresponds to situations where
the range is used as an iterator, or for indexing.

## Further Reading

* [Clippy - range_minus_one](https://clippy.rust-lang.org/stable/index.html#range_minus_one)

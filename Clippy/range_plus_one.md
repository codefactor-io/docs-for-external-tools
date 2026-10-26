Pattern: Exclusive range with upper bound plus one

Issue: -

## Description

The code is more readable with an inclusive range
like `x..=y`.

## What it does

Checks for exclusive ranges where 1 is added to the
upper bound, e.g., `x..(y+1)`.

## Examples

Example of **incorrect** code:

```rust
for i in x..(y+1) {
    // ..
}
```

Example of **correct** code:

```rust
for i in x..=y {
    // ..
}
```

## Limitations

The lint is conservative and will trigger only when switching
from an exclusive to an inclusive range is provably safe from
a typing point of view. This corresponds to situations where
the range is used as an iterator, or for indexing.

## Known problems

Will add unnecessary pair of parentheses when the
expression is not wrapped in a pair but starts with an opening parenthesis
and ends with a closing one.
I.e., `let _ = (f()+1)..(f()+1)` results in `let _ = ((f()+1)..=f())`.

Also in many cases, inclusive ranges are still slower to run than
exclusive ranges, because they essentially add an extra branch that
LLVM may fail to hoist out of the loop.

## Further Reading

* [Clippy - range_plus_one](https://clippy.rust-lang.org/stable/index.html#range_plus_one)

Pattern: Pointless comparison with min or max value

Issue: -

## Description

An expression like `min <= x` may misleadingly imply
that it is possible for `x` to be less than the minimum. Expressions like
`max < x` are probably mistakes.

## What it does

Checks for comparisons where one side of the relation is
either the minimum or maximum value for its type and warns if it involves a
case that is always true or always false. Only integer and boolean types are
checked.

## Examples

Example of **incorrect** code:

```rust
let vec: Vec<isize> = Vec::new();
if vec.len() <= 0 {}
if 100 > i32::MAX {}
```

## Known problems

For `usize` the size of the current compile target will
be assumed (e.g., 64 bits on 64 bit systems). This means code that uses such
a comparison to detect target pointer width will trigger this lint. One can
use `mem::sizeof` and compare its value or conditional compilation
attributes
like `#[cfg(target_pointer_width = "64")] ..` instead.

## Further Reading

* [Clippy - absurd_extreme_comparisons](https://clippy.rust-lang.org/stable/index.html#absurd_extreme_comparisons)

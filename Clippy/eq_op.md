Pattern: Identical operands on both sides of operator

Issue: -

## Description

This is usually just a typo or a copy and paste error.

## What it does

Checks for equal operands to comparison, logical and
bitwise, difference and division binary operators (`==`, `>`, etc., `&&`,
`||`, `&`, `|`, `^`, `-` and `/`).

## Examples

Example of **incorrect** code:

```rust
if x + 1 == x + 1 {}

// or

assert_eq!(a, a);
```

## Known problems

False negatives: We had some false positives regarding
calls (notably [racer](https://github.com/phildawes/racer) had one instance
of `x.pop() && x.pop()`), so we removed matching any function or method
calls. We may introduce a list of known pure functions in the future.

## Further Reading

* [Clippy - eq_op](https://clippy.rust-lang.org/stable/index.html#eq_op)

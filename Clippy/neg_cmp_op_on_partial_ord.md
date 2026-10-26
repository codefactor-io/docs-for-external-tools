Pattern: Negated comparison on partially ordered type

Issue: -

## Description

These operators make it easy to forget that the underlying types actually allow not only three
potential Orderings (Less, Equal, Greater) but also a fourth one (Uncomparable). This is
especially easy to miss if the operator based comparison result is negated.

## What it does

Checks for the usage of negated comparison operators on types which only implement
`PartialOrd` (e.g., `f64`).

## Examples

Example of **incorrect** code:

```rust
let a = 1.0;
let b = f64::NAN;

let not_less_or_equal = !(a <= b);
```

Example of **correct** code:

```rust
use std::cmp::Ordering;

let _not_less_or_equal = match a.partial_cmp(&b) {
    None | Some(Ordering::Greater) => true,
    _ => false,
};
```

## Further Reading

* [Clippy - neg_cmp_op_on_partial_ord](https://clippy.rust-lang.org/stable/index.html#neg_cmp_op_on_partial_ord)

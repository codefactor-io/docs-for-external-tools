Pattern: Read and write order depends on evaluation

Issue: -

## Description

While [the evaluation order of sub-expressions] is fully specified in Rust,
it still may be confusing to read an expression where the evaluation order
affects its behavior.

## What it does

Checks for a read and a write to the same variable where
whether the read occurs before or after the write depends on the evaluation
order of sub-expressions.

## Examples

```rust
let mut x = 0;

let a = {
    x = 1;
    1
} + x;
// Unclear whether a is 1 or 2.
```

Use instead:
```rust
let tmp = {
    x = 1;
    1
};
let a = tmp + x;
```

[order]: (https://doc.rust-lang.org/reference/expressions.html?highlight=subexpression#evaluation-order-of-operands)

## Known problems

Code which intentionally depends on the evaluation
order, or which is correct for any evaluation order.

## Further Reading

* [Clippy - mixed_read_write_in_expression](https://clippy.rust-lang.org/stable/index.html#mixed_read_write_in_expression)

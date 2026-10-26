Pattern: Redundant full-range slicing

Issue: -

## Description

It unnecessarily adds complexity to the expression.

## What it does

Checks for redundant slicing expressions which use the full range, and
do not change the type.

## Examples

Example of **incorrect** code:

```rust
fn get_slice(x: &[u32]) -> &[u32] {
    &x[..]
}
```

Example of **correct** code:

```rust
fn get_slice(x: &[u32]) -> &[u32] {
    x
}
```

## Known problems

If the type being sliced has an implementation of `Index<RangeFull>`
that actually changes anything then it can't be removed. However, this would be surprising
to people reading the code and should have a note with it.

## Further Reading

* [Clippy - redundant_slicing](https://clippy.rust-lang.org/stable/index.html#redundant_slicing)

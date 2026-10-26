Pattern: Reversed empty range

Issue: -

## Description

Empty ranges yield no values so iterating them is a no-op.
Moreover, trying to use a reversed range to index a slice will panic at run-time.

## What it does

Checks for range expressions `x..y` where both `x` and `y`
are constant and `x` is greater to `y`. Also triggers if `x` is equal to `y` when they are conditions to a `for` loop.

## Examples

Example of **incorrect** code:

```rust
fn main() {
    (10..=0).for_each(|x| println!("{}", x));

    let arr = [1, 2, 3, 4, 5];
    let sub = &arr[3..1];
}
```

Example of **correct** code:

```rust
fn main() {
    (0..=10).rev().for_each(|x| println!("{}", x));

    let arr = [1, 2, 3, 4, 5];
    let sub = &arr[1..3];
}
```

## Further Reading

* [Clippy - reversed_empty_ranges](https://clippy.rust-lang.org/stable/index.html#reversed_empty_ranges)

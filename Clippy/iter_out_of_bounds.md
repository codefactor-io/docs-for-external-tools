Pattern: Out of bounds `take()` or `skip()`

Issue: -

## Description

Taking or skipping more items than there are in an iterator either creates an iterator
with all items from the original iterator or an iterator with no items at all.
This is most likely not what the user intended to do.

## What it does

Looks for iterator combinator calls such as `.take(x)` or `.skip(x)`
where `x` is greater than the amount of items that an iterator will produce.

## Examples

Example of **incorrect** code:

```rust
for _ in [1, 2, 3].iter().take(4) {}
```

Example of **correct** code:

```rust
for _ in [1, 2, 3].iter() {}
```

## Further Reading

* [Clippy - iter_out_of_bounds](https://clippy.rust-lang.org/stable/index.html#iter_out_of_bounds)

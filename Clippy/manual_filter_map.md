Pattern: Missing use of `filter_map()`

Issue: -

## Description

Redundant code in the `filter` and `map` operations is poor style and
less performant.

## What it does

Checks for usage of `_.filter(_).map(_)` that can be written more simply
as `filter_map(_)`.

## Examples

Example of **incorrect** code:

```rust
(0_i32..10)
    .filter(|n| n.checked_add(1).is_some())
    .map(|n| n.checked_add(1).unwrap());
```

Example of **correct** code:

```rust
(0_i32..10).filter_map(|n| n.checked_add(1));
```

## Further Reading

* [Clippy - manual_filter_map](https://clippy.rust-lang.org/stable/index.html#manual_filter_map)

Pattern: Missing use of `find_map()`

Issue: -

## Description

Redundant code in the `find` and `map` operations is poor style and
less performant.

## What it does

Checks for usage of `_.find(_).map(_)` that can be written more simply
as `find_map(_)`.

## Examples

Example of **incorrect** code:

```rust
(0_i32..10)
    .find(|n| n.checked_add(1).is_some())
    .map(|n| n.checked_add(1).unwrap());
```

Example of **correct** code:

```rust
(0_i32..10).find_map(|n| n.checked_add(1));
```

## Further Reading

* [Clippy - manual_find_map](https://clippy.rust-lang.org/stable/index.html#manual_find_map)

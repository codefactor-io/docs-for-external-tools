Pattern: Use of `flat_map()` returning `Option`

Issue: -

## Description

`filter_map()` is known to always produce 0 or 1 output items per input item,
rather than however many the inner iterator type produces.
Therefore, it maintains the upper bound in `Iterator::size_hint()`,
and communicates to the reader that the input items are not being expanded into
multiple output items without their having to notice that the mapping function
returns an `Option`.

## What it does

Checks for usage of `Iterator::flat_map()` where `filter_map()` could be
used instead.

## Examples

Example of **incorrect** code:

```rust
let nums: Vec<i32> = ["1", "2", "whee!"].iter().flat_map(|x| x.parse().ok()).collect();
```

Example of **correct** code:

```rust
let nums: Vec<i32> = ["1", "2", "whee!"].iter().filter_map(|x| x.parse().ok()).collect();
```

## Further Reading

* [Clippy - flat_map_option](https://clippy.rust-lang.org/stable/index.html#flat_map_option)

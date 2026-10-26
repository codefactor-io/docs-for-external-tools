Pattern: `map()` over range with unused argument

Issue: -

## Description

It expresses the intent more clearly to `take` the correct number of times
from a generating function than to apply a closure to each number in a
range only to discard them.

## What it does

Checks for `Iterator::map` over ranges without using the parameter which
could be more clearly expressed using `std::iter::repeat(...).take(...)`
or `std::iter::repeat_n`.

## Examples

Example of **incorrect** code:

```rust
let random_numbers : Vec<_> = (0..10).map(|_| { 3 + 1 }).collect();
```

Example of **correct** code:

```rust
let f : Vec<_> = std::iter::repeat( 3 + 1 ).take(10).collect();
```

## Known Issues

This lint may suggest replacing a `Map<Range>` with a `Take<RepeatWith>`.
The former implements some traits that the latter does not, such as
`DoubleEndedIterator`.

## Further Reading

* [Clippy - map_with_unused_argument_over_ranges](https://clippy.rust-lang.org/stable/index.html#map_with_unused_argument_over_ranges)

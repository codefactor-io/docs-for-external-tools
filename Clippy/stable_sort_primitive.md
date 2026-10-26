Pattern: Stable sort of primitive values

Issue: -

## Description

Typically, using a stable sort consumes more memory and cpu cycles.
Because values which compare equal are identical, preserving their
relative order (the guarantee that a stable sort provides) means
nothing, while the extra costs still apply.

## What it does

When sorting primitive values (integers, bools, chars, as well
as arrays, slices, and tuples of such items), it is typically better to
use an unstable sort than a stable sort.

## Examples

Example of **incorrect** code:

```rust
let mut vec = vec![2, 1, 3];
vec.sort();
```

Example of **correct** code:

```rust
let mut vec = vec![2, 1, 3];
vec.sort_unstable();
```

## Known problems

As pointed out in
[issue #8241](https://github.com/rust-lang/rust-clippy/issues/8241),
a stable sort can instead be significantly faster for certain scenarios
(eg. when a sorted vector is extended with new data and resorted).

For more information and benchmarking results, please refer to the
issue linked above.

## Further Reading

* [Clippy - stable_sort_primitive](https://clippy.rust-lang.org/stable/index.html#stable_sort_primitive)

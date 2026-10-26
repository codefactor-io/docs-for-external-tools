Pattern: Naive byte count

Issue: -

## Description

The [`bytecount`](https://crates.io/crates/bytecount)
crate has methods to count your bytes faster, especially for large slices.

## What it does

Checks for naive byte counts

## Examples

Example of **incorrect** code:

```rust
let count = vec.iter().filter(|x| **x == 0u8).count();
```

Example of **correct** code:

```rust
let count = bytecount::count(&vec, 0u8);
```

## Known problems

If you have predominantly small slices, the
`bytecount::count(..)` method may actually be slower. However, if you can
ensure that less than 2³²-1 matches arise, the `naive_count_32(..)` can be
faster in those cases.

## Further Reading

* [Clippy - naive_bytecount](https://clippy.rust-lang.org/stable/index.html#naive_bytecount)

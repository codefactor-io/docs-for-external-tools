Pattern: Large enum variant

Issue: -

## Description

Enum size is bounded by the largest variant. Having one
large variant can penalize the memory layout of that enum.

## What it does

Checks for large size differences between variants on
`enum`s.

## Examples

Example of **incorrect** code:

```rust
enum Test {
    A(i32),
    B([i32; 8000]),
}
```

Example of **correct** code:

```rust
// Possibly better
enum Test2 {
    A(i32),
    B(Box<[i32; 8000]>),
}
```

## Known problems

This lint obviously cannot take the distribution of
variants in your running program into account. It is possible that the
smaller variants make up less than 1% of all instances, in which case
the overhead is negligible and the boxing is counter-productive. Always
measure the change this lint suggests.

For types that implement `Copy`, the suggestion to `Box` a variant's
data would require removing the trait impl. The types can of course
still be `Clone`, but that is worse ergonomically. Depending on the
use case it may be possible to store the large data in an auxiliary
structure (e.g. Arena or ECS).

The lint will ignore the impact of generic types to the type layout by
assuming every type parameter is zero-sized. Depending on your use case,
this may lead to a false positive.

## Further Reading

* [Clippy - large_enum_variant](https://clippy.rust-lang.org/stable/index.html#large_enum_variant)

Pattern: Missing use of `NonZero` conversion

Issue: -

## Description

Converting from `NonZero` types to regular integer types and then back to `NonZero`
types is less efficient and loses the type-safety guarantees provided by `NonZero` types.
Using `NonZero` types consistently can lead to more optimized code and prevent
certain classes of errors related to zero values.

## What it does

Checks for conversions from `NonZero` types to regular integer types,
and suggests using `NonZero` types for the target as well.

## Examples

Example of **incorrect** code:

```rust
use std::num::{NonZeroU32, NonZeroU64};

fn example(x: u64, y: NonZeroU32) {
    // Bad: Converting NonZeroU32 to u64 unnecessarily
    let r1 = x / u64::from(y.get());
    let r2 = x % u64::from(y.get());
}
```

Example of **correct** code:

```rust
use std::num::{NonZeroU32, NonZeroU64};

fn example(x: u64, y: NonZeroU32) {
    // Good: Preserving the NonZero property
    let r1 = x / NonZeroU64::from(y);
    let r2 = x % NonZeroU64::from(y);
}
```

## Further Reading

* [Clippy - non_zero_suggestions](https://clippy.rust-lang.org/stable/index.html#non_zero_suggestions)

Pattern: Owned value created only for comparison

Issue: -

## Description

The comparison can operate on a reference, so creating
an owned value effectively throws it away directly afterwards, which is
needlessly consuming code and heap space.

## What it does

Checks for conversions to owned values just for the sake
of a comparison.

## Examples

Example of **incorrect** code:

```rust
if x.to_owned() == y {}
```

Example of **correct** code:

```rust
if x == y {}
```

## Further Reading

* [Clippy - cmp_owned](https://clippy.rust-lang.org/stable/index.html#cmp_owned)

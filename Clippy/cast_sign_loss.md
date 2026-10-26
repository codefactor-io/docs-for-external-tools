Pattern: Cast from signed to unsigned type

Issue: -

## Description

Possibly surprising results. You can activate this lint
as a one-time check to see where numeric wrapping can arise.

## What it does

Checks for casts from a signed to an unsigned numeric
type. In this case, negative values wrap around to large positive values,
which can be quite surprising in practice. However, since the cast works as
defined, this lint is `Allow` by default.

## Examples

Example of **incorrect** code:

```rust
let y: i8 = -1;
y as u64; // will return 18446744073709551615
```

## Further Reading

* [Clippy - cast_sign_loss](https://clippy.rust-lang.org/stable/index.html#cast_sign_loss)

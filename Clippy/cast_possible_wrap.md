Pattern: Possibly wrapping cast from unsigned to signed

Issue: -

## Description

While such a cast is not bad in itself, the results can
be surprising when this is not the intended behavior:

## What it does

Checks for casts from an unsigned type to a signed type of
the same size, or possibly smaller due to target-dependent integers.
Performing such a cast is a no-op for the compiler (that is, nothing is
changed at the bit level), and the binary representation of the value is
reinterpreted. This can cause wrapping if the value is too big
for the target signed type. However, the cast works as defined, so this lint
is `Allow` by default.

## Examples

```rust
let _ = u32::MAX as i32; // will yield a value of `-1`
```

Use instead:
```rust
let _ = i32::try_from(u32::MAX).ok();
```

If the wrapping is intended, you can use:
```rust
let _ = u32::MAX.cast_signed();
let _ = (-1i32).cast_unsigned();
```

## Further Reading

* [Clippy - cast_possible_wrap](https://clippy.rust-lang.org/stable/index.html#cast_possible_wrap)

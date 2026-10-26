Pattern: Bit mask instead of `trailing_zeros()`

Issue: -

## Description

`x.trailing_zeros() >= 4` is much clearer than `x & 15
== 0`

## What it does

Checks for bit masks that can be replaced by a call
to `trailing_zeros`

## Examples

Example of **incorrect** code:

```rust
if x & 0b1111 == 0 { }
```

Example of **correct** code:

```rust
if x.trailing_zeros() >= 4 { }
```

## Further Reading

* [Clippy - verbose_bit_mask](https://clippy.rust-lang.org/stable/index.html#verbose_bit_mask)

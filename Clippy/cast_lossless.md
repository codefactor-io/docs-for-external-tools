Pattern: Lossless numeric cast with `as`

Issue: -

## Description

Rust's `as` keyword will perform many kinds of conversions, including
silently lossy conversions. Conversion functions such as `i32::from`
will only perform lossless conversions. Using the conversion functions
prevents conversions from becoming silently lossy if the input types
ever change, and makes it clear for people reading the code that the
conversion is lossless.

## What it does

Checks for casts between numeric types that can be replaced by safe
conversion functions.

## Examples

```rust
fn as_u64(x: u8) -> u64 {
    x as u64
}
```

Using `::from` would look like this:

```rust
fn as_u64(x: u8) -> u64 {
    u64::from(x)
}
```

## Further Reading

* [Clippy - cast_lossless](https://clippy.rust-lang.org/stable/index.html#cast_lossless)

Pattern: Cast of character literal to `u8`

Issue: -

## Description

In general, casting values to smaller types is
error-prone and should be avoided where possible. In the particular case of
converting a character literal to `u8`, it is easy to avoid by just using a
byte literal instead. As an added bonus, `b'a'` is also slightly shorter
than `'a' as u8`.

## What it does

Checks for expressions where a character literal is cast
to `u8` and suggests using a byte literal instead.

## Examples

```rust
'x' as u8
```

A better version, using the byte literal:

```rust
b'x'
```

## Further Reading

* [Clippy - char_lit_as_u8](https://clippy.rust-lang.org/stable/index.html#char_lit_as_u8)

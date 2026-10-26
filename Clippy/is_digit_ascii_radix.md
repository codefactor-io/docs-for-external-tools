Pattern: Use of `is_digit()` with radix 10 or 16

Issue: -

## Description

`is_digit(..)` is slower and requires specifying the radix.

## What it does

Finds usages of [`char::is_digit`](https://doc.rust-lang.org/stable/std/primitive.char.html#method.is_digit) that
can be replaced with [`is_ascii_digit`](https://doc.rust-lang.org/stable/std/primitive.char.html#method.is_ascii_digit) or
[`is_ascii_hexdigit`](https://doc.rust-lang.org/stable/std/primitive.char.html#method.is_ascii_hexdigit).

## Examples

Example of **incorrect** code:

```rust
let c: char = '6';
c.is_digit(10);
c.is_digit(16);
```

Example of **correct** code:

```rust
let c: char = '6';
c.is_ascii_digit();
c.is_ascii_hexdigit();
```

## Further Reading

* [Clippy - is_digit_ascii_radix](https://clippy.rust-lang.org/stable/index.html#is_digit_ascii_radix)

Pattern: Transmute from `&[u8]` to `&str`

Issue: -

## Description

Not every byte slice is a valid UTF-8 string.

## What it does

Checks for transmutes from a `&[u8]` to a `&str`.

## Examples

```rust
let b: &[u8] = &[1_u8, 2_u8];
unsafe {
    let _: &str = std::mem::transmute(b); // where b: &[u8]
}

// should be:
let _ = std::str::from_utf8(b).unwrap();
```

## Known problems

- [`from_utf8`] which this lint suggests using is slower than `transmute`
as it needs to validate the input.
If you are certain that the input is always a valid UTF-8,
use [`from_utf8_unchecked`] which is as fast as `transmute`
but has a semantically meaningful name.
- You might want to handle errors returned from [`from_utf8`] instead of calling `unwrap`.

[`from_utf8`]: https://doc.rust-lang.org/std/str/fn.from_utf8.html
[`from_utf8_unchecked`]: https://doc.rust-lang.org/std/str/fn.from_utf8_unchecked.html

## Further Reading

* [Clippy - transmute_bytes_to_str](https://clippy.rust-lang.org/stable/index.html#transmute_bytes_to_str)

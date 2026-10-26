Pattern: Use of `bytes().count()` instead of `len()`

Issue: -

## Description

`str::bytes().count()` is longer and may not be as performant as using
`str::len()`.

## What it does

It checks for `str::bytes().count()` and suggests replacing it with
`str::len()`.

## Examples

Example of **incorrect** code:

```rust
"hello".bytes().count();
String::from("hello").bytes().count();
```

Example of **correct** code:

```rust
"hello".len();
String::from("hello").len();
```

## Further Reading

* [Clippy - bytes_count_to_len](https://clippy.rust-lang.org/stable/index.html#bytes_count_to_len)

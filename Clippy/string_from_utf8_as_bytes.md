Pattern: String converted to bytes and back

Issue: -

## Description

It's unnecessary, the string can be used directly.

## What it does

Check if the string is transformed to byte array and cast back to string.

## Examples

Example of **incorrect** code:

```rust
std::str::from_utf8(&"Hello World!".as_bytes()[6..11]).unwrap();
```

Example of **correct** code:

```rust
&"Hello World!"[6..11];
```

## Further Reading

* [Clippy - string_from_utf8_as_bytes](https://clippy.rust-lang.org/stable/index.html#string_from_utf8_as_bytes)

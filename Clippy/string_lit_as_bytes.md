Pattern: `as_bytes()` on string literal

Issue: -

## Description

Byte string literals (e.g., `b"foo"`) can be used
instead. They are shorter but less discoverable than `as_bytes()`.

## What it does

Checks for the `as_bytes` method called on string literals
that contain only ASCII characters.

## Examples

Example of **incorrect** code:

```rust
let bstr = "a byte string".as_bytes();
```

Example of **correct** code:

```rust
let bstr = b"a byte string";
```

## Known problems

`"str".as_bytes()` and the suggested replacement of `b"str"` are not
equivalent because they have different types. The former is `&[u8]`
while the latter is `&[u8; 3]`. That means in general they will have a
different set of methods and different trait implementations.

```rust
fn f(v: Vec<u8>) {}

f("...".as_bytes().to_owned()); // works
f(b"...".to_owned()); // does not work, because arg is [u8; 3] not Vec<u8>

fn g(r: impl std::io::Read) {}

g("...".as_bytes()); // works
g(b"..."); // does not work
```

The actual equivalent of `"str".as_bytes()` with the same type is not
`b"str"` but `&b"str"[..]`, which is a great deal of punctuation and not
more readable than a function call.

## Further Reading

* [Clippy - string_lit_as_bytes](https://clippy.rust-lang.org/stable/index.html#string_lit_as_bytes)

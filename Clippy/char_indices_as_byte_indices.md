Pattern: Character position used as byte index

Issue: -

## Description

A character (more specifically, a Unicode scalar value) that is yielded by `str::chars` can take up multiple bytes,
so a character position does not necessarily have the same byte index at which the character is stored.
Thus, using the character position where a byte index is expected can unexpectedly return wrong values
or panic when the string consists of multibyte characters.

For example, the character `a` in `äa` is stored at byte index 2 but has the character position 1.
Using the character position 1 to index into the string will lead to a panic as it is in the middle of the first character.

Instead of `.chars().enumerate()`, the correct iterator to use is `.char_indices()`, which yields byte indices.

This pattern is technically fine if the strings are known to only use the ASCII subset,
though in those cases it would be better to use `bytes()` directly to make the intent clearer,
but there is also no downside to just using `.char_indices()` directly and supporting non-ASCII strings.

You may also want to read the [chapter on strings in the Rust Book](https://doc.rust-lang.org/book/ch08-02-strings.html)
which goes into this in more detail.

## What it does

Checks for usage of a character position yielded by `.chars().enumerate()` in a context where a **byte index** is expected,
such as an argument to a specific `str` method or indexing into a `str` or `String`.

## Examples

Example of **incorrect** code:

```rust
for (idx, c) in s.chars().enumerate() {
    let _ = s[idx..]; // ⚠️ Panics for strings consisting of multibyte characters
}
```

Example of **correct** code:

```rust
for (idx, c) in s.char_indices() {
    let _ = s[idx..];
}
```

## Further Reading

* [Clippy - char_indices_as_byte_indices](https://clippy.rust-lang.org/stable/index.html#char_indices_as_byte_indices)

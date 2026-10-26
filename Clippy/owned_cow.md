Pattern: Unnecessary owned type in `Cow`

Issue: -

## Description

The borrowed types are usually more flexible, in that e.g. a
`Cow<'_, str>` can accept both `&str` and `String` while
`Cow<'_, String>` can only accept `&String` and `String`. In
particular, `&str` is more general, because it allows for string
literals while `&String` can only be borrowed from a heap-owned
`String`).

## What it does

Detects needlessly owned `Cow` types.

## Examples

Example of **incorrect** code:

```rust
let wrogn: std::borrow::Cow<'_, Vec<u8>>;
```

Example of **correct** code:

```rust
let right: std::borrow::Cow<'_, [u8]>;
```

## Known Problems

The lint does not check for usage of the type. There may be external
interfaces that require the use of an owned type.

At least the `CString` type also has a different API than `CStr`: The
former has an `as_bytes` method which the latter calls `to_bytes`.
There is no guarantee that other types won't gain additional methods
leading to a similar mismatch.

In addition, the lint only checks for the known problematic types
`String`, `Vec<_>`, `CString`, `OsString` and `PathBuf`. Custom types
that implement `ToOwned` will not be detected.

## Further Reading

* [Clippy - owned_cow](https://clippy.rust-lang.org/stable/index.html#owned_cow)

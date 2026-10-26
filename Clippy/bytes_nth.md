Pattern: Use of `.bytes().nth()`

Issue: -

## Description

`.as_bytes().get()` is more efficient and more
readable.

## What it does

Checks for the use of `.bytes().nth()`.

## Examples

Example of **incorrect** code:

```rust
"Hello".bytes().nth(3);
```

Example of **correct** code:

```rust
"Hello".as_bytes().get(3);
```

## Further Reading

* [Clippy - bytes_nth](https://clippy.rust-lang.org/stable/index.html#bytes_nth)

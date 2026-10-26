Pattern: Unnecessary raw string literal

Issue: -

## Description

For consistent style by using simpler string literals whenever possible.

However, there are many cases where using a raw string literal is more
idiomatic than a string literal, so it's opt-in.

## What it does

Checks for raw string literals where a string literal can be used instead.

## Examples

Example of **incorrect** code:

```rust
let r = r"Hello, world!";
```

Example of **correct** code:

```rust
let r = "Hello, world!";
```

## Further Reading

* [Clippy - needless_raw_strings](https://clippy.rust-lang.org/stable/index.html#needless_raw_strings)

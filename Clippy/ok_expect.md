Pattern: Use of `ok().expect()`

Issue: -

## Description

Because you usually call `expect()` on the `Result`
directly to get a better error message.

## What it does

Checks for usage of `ok().expect(..)`.

Note: This lint only triggers for code marked compatible
with versions of the compiler older than Rust 1.82.0.

## Examples

Example of **incorrect** code:

```rust
x.ok().expect("why did I do this again?");
```

Example of **correct** code:

```rust
x.expect("why did I do this again?");
```

## Further Reading

* [Clippy - ok_expect](https://clippy.rust-lang.org/stable/index.html#ok_expect)

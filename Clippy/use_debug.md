Pattern: Use of `Debug` formatting

Issue: -

## Description

The purpose of the `Debug` trait is to facilitate debugging Rust code,
and [no guarantees are made about its output][stability].
It should not be used in user-facing output.

## What it does

Checks for usage of `Debug` formatting. The purpose of this
lint is to catch debugging remnants.

## Examples

```rust
println!("{:?}", foo);
```

[stability]: https://doc.rust-lang.org/stable/std/fmt/trait.Debug.html#stability

## Further Reading

* [Clippy - use_debug](https://clippy.rust-lang.org/stable/index.html#use_debug)

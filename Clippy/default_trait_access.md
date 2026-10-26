Pattern: Use of `Default::default()`

Issue: -

## Description

It's easier for the reader if the name of the type is used, rather than the
generic `Default`.

## What it does

Checks for literal calls to `Default::default()`.

## Examples

Example of **incorrect** code:

```rust
let s: String = Default::default();
```

Example of **correct** code:

```rust
let s = String::default();
```

## Further Reading

* [Clippy - default_trait_access](https://clippy.rust-lang.org/stable/index.html#default_trait_access)

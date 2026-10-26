Pattern: Missing use of `Box::default()`

Issue: -

## Description

`Box::default()` is equivalent and more concise.

## What it does

checks for `Box::new(Default::default())`, which can be written as
`Box::default()`.

## Examples

Example of **incorrect** code:

```rust
let x: Box<String> = Box::new(Default::default());
```

Example of **correct** code:

```rust
let x: Box<String> = Box::default();
```

## Further Reading

* [Clippy - box_default](https://clippy.rust-lang.org/stable/index.html#box_default)

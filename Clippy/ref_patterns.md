Pattern: Use of `ref` pattern

Issue: -

## Description

The `ref` keyword can be confusing for people unfamiliar with it, and often
it is more concise to use `&` instead.

## What it does

Checks for usages of the `ref` keyword.

## Examples

Example of **incorrect** code:

```rust
let opt = Some(5);
if let Some(ref foo) = opt {}
```

Example of **correct** code:

```rust
let opt = Some(5);
if let Some(foo) = &opt {}
```

## Further Reading

* [Clippy - ref_patterns](https://clippy.rust-lang.org/stable/index.html#ref_patterns)

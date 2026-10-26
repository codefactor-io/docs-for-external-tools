Pattern: Unnecessary `&ref` pattern

Issue: -

## Description

This pattern has no effect in almost all cases.

## What it does

Checks for bindings that needlessly destructure a reference and borrow the inner
value with `&ref`.

## Examples

Example of **incorrect** code:

```rust
let mut v = Vec::<String>::new();
v.iter_mut().filter(|&ref a| a.is_empty());

if let &[ref first, ref second] = v.as_slice() {}
```

Example of **correct** code:

```rust
let mut v = Vec::<String>::new();
v.iter_mut().filter(|a| a.is_empty());

if let [first, second] = v.as_slice() {}
```

## Further Reading

* [Clippy - needless_borrowed_reference](https://clippy.rust-lang.org/stable/index.html#needless_borrowed_reference)

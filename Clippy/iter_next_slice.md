Pattern: Use of `iter().next()` on slice

Issue: -

## Description

These can be shortened into `.first()` or `.first_mut()`

## What it does

Checks for usage of `iter().next()` or `iter_mut().next()` on a Slice or an Array

## Examples

Example of **incorrect** code:

```rust
a[2..].iter().next();
b.iter().next();
c.iter_mut().next();
```

Example of **correct** code:

```rust
a.get(2);
b.first();
c.first_mut();
```

## Further Reading

* [Clippy - iter_next_slice](https://clippy.rust-lang.org/stable/index.html#iter_next_slice)

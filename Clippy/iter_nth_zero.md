Pattern: Use of `nth(0)` on iterator

Issue: -

## Description

`iter.next()` is equivalent to
`iter.nth(0)`, as they both consume the next element,
 but is more readable.

## What it does

Checks for the use of `iter.nth(0)`.

## Examples

Example of **incorrect** code:

```rust
let x = s.iter().nth(0);
```

Example of **correct** code:

```rust
let x = s.iter().next();
```

## Further Reading

* [Clippy - iter_nth_zero](https://clippy.rust-lang.org/stable/index.html#iter_nth_zero)

Pattern: `map()` followed by `count()`

Issue: -

## Description

It looks suspicious. Maybe `map` was confused with `filter`.
If the `map` call is intentional, this should be rewritten
using `inspect`. Or, if you intend to drive the iterator to
completion, you can just use `for_each` instead.

## What it does

Checks for calls to `map` followed by a `count`.

## Examples

Example of **incorrect** code:

```rust
let _ = (0..3).map(|x| x + 2).count();
```

## Further Reading

* [Clippy - suspicious_map](https://clippy.rust-lang.org/stable/index.html#suspicious_map)

Pattern: `splitn()` with zero or one split

Issue: -

## Description

These calls don't actually split the value and are
likely to be intended as a different number.

## What it does

Checks for calls to [`splitn`]
(https://doc.rust-lang.org/std/primitive.str.html#method.splitn) and
related functions with either zero or one splits.

## Examples

Example of **incorrect** code:

```rust
for x in s.splitn(1, ":") {
    // ..
}
```

Example of **correct** code:

```rust
for x in s.splitn(2, ":") {
    // ..
}
```

## Further Reading

* [Clippy - suspicious_splitn](https://clippy.rust-lang.org/stable/index.html#suspicious_splitn)

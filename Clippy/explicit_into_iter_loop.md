Pattern: Unnecessary `into_iter()` in `for` loop

Issue: -

## Description

Readability.

## What it does

Checks for loops on `y.into_iter()` where `y` will do, and
suggests the latter.

## Examples

Example of **incorrect** code:

```rust
// with `y` a `Vec` or slice:
for x in y.into_iter() {
    // ..
}
```

Example of **correct** code:

```rust
for x in y {
    // ..
}
```

## Further Reading

* [Clippy - explicit_into_iter_loop](https://clippy.rust-lang.org/stable/index.html#explicit_into_iter_loop)

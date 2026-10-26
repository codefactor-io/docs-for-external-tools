Pattern: Unnecessary `iter()` in `for` loop

Issue: -

## Description

Readability.

## What it does

Checks for loops on `x.iter()` where `&x` will do, and
suggests the latter.

## Examples

Example of **incorrect** code:

```rust
// with `y` a `Vec` or slice:
for x in y.iter() {
    // ..
}
```

Example of **correct** code:

```rust
for x in &y {
    // ..
}
```

## Known problems

False negatives. We currently only warn on some known
types.

## Further Reading

* [Clippy - explicit_iter_loop](https://clippy.rust-lang.org/stable/index.html#explicit_iter_loop)

Pattern: `if let` instead of equality check

Issue: -

## Description

* It reads better and has less cognitive load because equality won't cause binding.
* It is a [Yoda condition](https://en.wikipedia.org/wiki/Yoda_conditions). Yoda conditions are widely
criticized for increasing the cognitive load of reading the code.
* Equality is a simple bool expression and can be merged with `&&` and `||` and
reuse if blocks

## What it does

Checks for pattern matchings that can be expressed using equality.

## Examples

Example of **incorrect** code:

```rust
if let Some(2) = x {
    do_thing();
}
```

Example of **correct** code:

```rust
if x == Some(2) {
    do_thing();
}
```

## Further Reading

* [Clippy - equatable_if_let](https://clippy.rust-lang.org/stable/index.html#equatable_if_let)

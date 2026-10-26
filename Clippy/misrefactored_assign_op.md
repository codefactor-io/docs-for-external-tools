Pattern: Variable on both sides of compound assignment

Issue: -

## Description

Most likely these are bugs where one meant to write `a
op= b`.

## What it does

Checks for `a op= a op b` or `a op= b op a` patterns.

## Examples

Example of **incorrect** code:

```rust
let mut a = 5;
let b = 2;
// ...
a += a + b;
```

## Known problems

Clippy cannot know for sure if `a op= a op b` should have
been `a = a op a op b` or `a = a op b`/`a op= b`. Therefore, it suggests both.
If `a op= a op b` is really the correct behavior it should be
written as `a = a op a op b` as it's less confusing.

## Further Reading

* [Clippy - misrefactored_assign_op](https://clippy.rust-lang.org/stable/index.html#misrefactored_assign_op)

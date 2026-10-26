Pattern: Missing use of compound assignment operator

Issue: -

## Description

These can be written as the shorter `a op= b`.

## What it does

Checks for `a = a op b` or `a = b commutative_op a`
patterns.

## Examples

Example of **incorrect** code:

```rust
let mut a = 5;
let b = 0;
// ...

a = a + b;
```

Example of **correct** code:

```rust
let mut a = 5;
let b = 0;
// ...

a += b;
```

## Known problems

While forbidden by the spec, `OpAssign` traits may have
implementations that differ from the regular `Op` impl.

## Further Reading

* [Clippy - assign_op_pattern](https://clippy.rust-lang.org/stable/index.html#assign_op_pattern)

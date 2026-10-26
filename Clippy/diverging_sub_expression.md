Pattern: Diverging sub-expression

Issue: -

## Description

It is often confusing to read. In addition, the
sub-expression evaluation order for Rust is not well documented.

## What it does

Checks for diverging calls that are not match arms or
statements.

## Examples

Example of **incorrect** code:

```rust
let a = b() || panic!() || c();
// `c()` is dead, `panic!()` is only called if `b()` returns `false`
let x = (a, b, c, panic!());
// can simply be replaced by `panic!()`
```

## Known problems

Someone might want to use `some_bool || panic!()` as a
shorthand.

## Further Reading

* [Clippy - diverging_sub_expression](https://clippy.rust-lang.org/stable/index.html#diverging_sub_expression)

Pattern: Assertion on constant value

Issue: -

## Description

Will be optimized out by the compiler or should probably be replaced by a
`panic!()` or `unreachable!()`

## What it does

Checks for `assert!(true)` and `assert!(false)` calls.

## Examples

Example of **incorrect** code:

```rust
assert!(false)
assert!(true)
const B: bool = false;
assert!(B)
```

## Further Reading

* [Clippy - assertions_on_constants](https://clippy.rust-lang.org/stable/index.html#assertions_on_constants)

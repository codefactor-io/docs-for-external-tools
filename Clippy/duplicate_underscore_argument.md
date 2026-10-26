Pattern: Argument names differing only by underscore

Issue: -

## Description

It affects code readability.

## What it does

Checks for function arguments having the similar names
differing by an underscore.

## Examples

Example of **incorrect** code:

```rust
fn foo(a: i32, _a: i32) {}
```

Example of **correct** code:

```rust
fn bar(a: i32, _b: i32) {}
```

## Further Reading

* [Clippy - duplicate_underscore_argument](https://clippy.rust-lang.org/stable/index.html#duplicate_underscore_argument)

Pattern: Unit value passed as argument

Issue: -

## Description

This is likely the result of an accidental semicolon.

## What it does

Checks for passing a unit value as an argument to a function without using a
unit literal (`()`).

## Examples

Example of **incorrect** code:

```rust
foo({
    let a = bar();
    baz(a);
})
```

## Further Reading

* [Clippy - unit_arg](https://clippy.rust-lang.org/stable/index.html#unit_arg)

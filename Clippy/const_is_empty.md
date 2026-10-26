Pattern: `is_empty()` on compile-time constant

Issue: -

## Description

String literals and constant values are known at compile time. Checking if they
are empty will always return the same value. This might not be the intention of
the expression.

## What it does

It identifies calls to `.is_empty()` on constant values.

## Examples

Example of **incorrect** code:

```rust
let value = "";
if value.is_empty() {
    println!("the string is empty");
}
```

Example of **correct** code:

```rust
println!("the string is empty");
```

## Further Reading

* [Clippy - const_is_empty](https://clippy.rust-lang.org/stable/index.html#const_is_empty)

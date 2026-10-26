Pattern: Excessive precision in float literal

Issue: -

## Description

Rust will truncate the literal silently.

## What it does

Checks for float literals with a precision greater
than that supported by the underlying type.

The lint is suppressed for literals with over `const_literal_digits_threshold` digits.

## Examples

Example of **incorrect** code:

```rust
let v: f32 = 0.123_456_789_9;
println!("{}", v); //  0.123_456_789
```

Example of **correct** code:

```rust
let v: f64 = 0.123_456_789_9;
println!("{}", v); //  0.123_456_789_9
```

## Further Reading

* [Clippy - excessive_precision](https://clippy.rust-lang.org/stable/index.html#excessive_precision)

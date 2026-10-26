Pattern: Use of `as _` conversion

Issue: -

## Description

The conversion might include lossy conversion or a dangerous cast that might go
undetected due to the type being inferred.

The lint is allowed by default as using `_` is less wordy than always specifying the type.

## What it does

Checks for the usage of `as _` conversion using inferred type.

## Examples

Example of **incorrect** code:

```rust
fn foo(n: usize) {}
let n: u16 = 256;
foo(n as _);
```

Example of **correct** code:

```rust
fn foo(n: usize) {}
let n: u16 = 256;
foo(n as usize);
```

## Further Reading

* [Clippy - as_underscore](https://clippy.rust-lang.org/stable/index.html#as_underscore)

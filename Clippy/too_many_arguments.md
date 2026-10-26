Pattern: Too many function arguments

Issue: -

## Description

Functions with lots of parameters are considered bad
style and reduce readability (“what does the 5th parameter mean?”). Consider
grouping some parameters into a new type.

## What it does

Checks for functions with too many parameters.

## Examples

Example of **incorrect** code:

```rust
fn foo(x: u32, y: u32, name: &str, c: Color, w: f32, h: f32, a: f32, b: f32) {
    // ..
}
```

## Further Reading

* [Clippy - too_many_arguments](https://clippy.rust-lang.org/stable/index.html#too_many_arguments)

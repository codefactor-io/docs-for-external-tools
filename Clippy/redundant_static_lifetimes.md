Pattern: Redundant `'static` lifetime on constant

Issue: -

## Description

Adding `'static` to every reference can create very
complicated types.

## What it does

Checks for constants and statics with an explicit `'static` lifetime.

## Examples

```rust
const FOO: &'static [(&'static str, &'static str, fn(&Bar) -> bool)] =
&[...]
static FOO: &'static [(&'static str, &'static str, fn(&Bar) -> bool)] =
&[...]
```
This code can be rewritten as
```rust
 const FOO: &[(&str, &str, fn(&Bar) -> bool)] = &[...]
 static FOO: &[(&str, &str, fn(&Bar) -> bool)] = &[...]
```

## Further Reading

* [Clippy - redundant_static_lifetimes](https://clippy.rust-lang.org/stable/index.html#redundant_static_lifetimes)

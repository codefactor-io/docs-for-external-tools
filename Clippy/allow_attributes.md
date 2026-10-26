Pattern: Use of `#[allow]` instead of `#[expect]`

Issue: -

## Description

`#[expect]` attributes suppress the lint emission, but emit a warning, if
the expectation is unfulfilled. This can be useful to be notified when the
lint is no longer triggered.

## What it does

Checks for usage of the `#[allow]` attribute and suggests replacing it with
the `#[expect]` attribute (See [RFC 2383](https://rust-lang.github.io/rfcs/2383-lint-reasons.html))

This lint only warns outer attributes (`#[allow]`), as inner attributes
(`#![allow]`) are usually used to enable or disable lints on a global scale.

## Examples

Example of **incorrect** code:

```rust
#[allow(unused_mut)]
fn foo() -> usize {
    let mut a = Vec::new();
    a.len()
}
```

Example of **correct** code:

```rust
#[expect(unused_mut)]
fn foo() -> usize {
    let mut a = Vec::new();
    a.len()
}
```

## Further Reading

* [Clippy - allow_attributes](https://clippy.rust-lang.org/stable/index.html#allow_attributes)

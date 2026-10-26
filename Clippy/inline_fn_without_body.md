Pattern: `#[inline]` on trait method without body

Issue: -

## Description

Only implementations of trait methods may be inlined.
The inline attribute is ignored for trait methods without bodies.

## What it does

Checks for `#[inline]` on trait methods without bodies

## Examples

Example of **incorrect** code:

```rust
trait Animal {
    #[inline]
    fn name(&self) -> &'static str;
}
```

## Further Reading

* [Clippy - inline_fn_without_body](https://clippy.rust-lang.org/stable/index.html#inline_fn_without_body)

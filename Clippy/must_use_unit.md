Pattern: `#[must_use]` on unit-returning function

Issue: -

## Description

Unit values are useless. The attribute is likely
a remnant of a refactoring that removed the return type.

## What it does

Checks for a `#[must_use]` attribute on
unit-returning functions and methods.

## Examples

Example of **incorrect** code:

```rust
#[must_use]
fn useless() { }
```

## Further Reading

* [Clippy - must_use_unit](https://clippy.rust-lang.org/stable/index.html#must_use_unit)

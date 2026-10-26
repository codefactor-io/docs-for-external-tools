Pattern: `#[allow]` or `#[expect]` without reason

Issue: -

## Description

Justifying each `allow` helps readers understand the reasoning,
and may allow removing `allow` attributes if their purpose is obsolete.

## What it does

Checks for attributes that allow lints without a reason.

## Examples

Example of **incorrect** code:

```rust
#![allow(clippy::some_lint)]
```

Example of **correct** code:

```rust
#![allow(clippy::some_lint, reason = "False positive rust-lang/rust-clippy#1002020")]
```

## Further Reading

* [Clippy - allow_attributes_without_reason](https://clippy.rust-lang.org/stable/index.html#allow_attributes_without_reason)

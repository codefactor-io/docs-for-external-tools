Pattern: `#[must_use]` value discarded with `let _`

Issue: -

## Description

To ensure that all `#[must_use]` types are used rather than ignored.

## What it does

Checks for `let _ = <expr>` where expr is `#[must_use]`

## Examples

Example of **incorrect** code:

```rust
fn f() -> Result<u32, u32> {
    Ok(0)
}

let _ = f();
// is_ok() is marked #[must_use]
let _ = f().is_ok();
```

## Further Reading

* [Clippy - let_underscore_must_use](https://clippy.rust-lang.org/stable/index.html#let_underscore_must_use)

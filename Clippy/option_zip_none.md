Pattern: `Option::zip()` with `None`

Issue: -

## Description

`Option::zip` with `None` always returns `None`.

## What it does

Checks for calls of the form `Option::zip(_, None)` or `Option::zip(None, _)`.

## Examples

Example of **incorrect** code:

```rust
let foo = Some(5);
foo.zip(None);
```

Example of **correct** code:

```rust
None
```

## Further Reading

* [Clippy - option_zip_none](https://clippy.rust-lang.org/stable/index.html#option_zip_none)

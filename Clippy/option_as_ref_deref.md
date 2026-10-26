Pattern: Missing use of `Option::as_deref()`

Issue: -

## Description

Readability, this can be written more concisely as
`_.as_deref()`.

## What it does

Checks for usage of `_.as_ref().map(Deref::deref)` or its aliases (such as String::as_str).

## Examples

Example of **incorrect** code:

```rust
opt.as_ref().map(String::as_str)
```

Example of **correct** code:

```rust
opt.as_deref()
```

## Further Reading

* [Clippy - option_as_ref_deref](https://clippy.rust-lang.org/stable/index.html#option_as_ref_deref)

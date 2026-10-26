Pattern: Missing use of `Option::as_slice()`

Issue: -

## Description

Those implementations are both more complex than calling `as_slice`
and unlike that incur a branch, pessimizing performance and leading
to more generated code.

## What it does

This detects various manual reimplementations of `Option::as_slice`.

## Examples

Example of **incorrect** code:

```rust
_ = opt.as_ref().map_or(&[][..], std::slice::from_ref);
_ = match opt.as_ref() {
    Some(f) => std::slice::from_ref(f),
    None => &[],
};
```

Example of **correct** code:

```rust
_ = opt.as_slice();
_ = opt.as_slice();
```

## Further Reading

* [Clippy - manual_option_as_slice](https://clippy.rust-lang.org/stable/index.html#manual_option_as_slice)

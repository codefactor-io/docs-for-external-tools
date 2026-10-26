Pattern: Unnecessary trailing comma in macro call

Issue: -

## Description

The trailing comma is redundant and removing it is more consistent with how
`rustfmt` formats regular function calls.

## What it does

Suggests removing an unnecessary trailing comma before the closing parenthesis in
single-line macro invocations.

## Examples

Example of **incorrect** code:

```rust
println!("Foo={}", 1,);
```

Example of **correct** code:

```rust
println!("Foo={}", 1);
```

## Known limitations

This lint currently only runs on format-like macros (e.g. `format!`, `println!`,
`write!`) because it relies on format-argument parsing; applying it to arbitrary
user macros could cause incorrect suggestions. It may be extended to other
macros in the future. Only single-line macro invocations are linted.

## Further Reading

* [Clippy - unnecessary_trailing_comma](https://clippy.rust-lang.org/stable/index.html#unnecessary_trailing_comma)

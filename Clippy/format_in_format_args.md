Pattern: Nested `format!` in formatting macro

Issue: -

## Description

The recommended code is both shorter and avoids a temporary allocation.

## What it does

Detects `format!` within the arguments of another macro that does
formatting such as `format!` itself, `write!` or `println!`. Suggests
inlining the `format!` call.

## Examples

Example of **incorrect** code:

```rust
println!("error: {}", format!("something failed at {}", Location::caller()));
```

Example of **correct** code:

```rust
println!("error: something failed at {}", Location::caller());
```

## Further Reading

* [Clippy - format_in_format_args](https://clippy.rust-lang.org/stable/index.html#format_in_format_args)

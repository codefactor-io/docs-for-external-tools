Pattern: Format specifier with no effect

Issue: -

## Description

Shorter format specifiers are easier to read, it may also indicate that
an expected formatting operation such as adding padding isn't happening.

## What it does

Detects [formatting parameters] that have no effect on the output of
`format!()`, `println!()` or similar macros.

This includes:
- Format specifiers on `format_args!()` (width, precision have no effect)
- Format width too small for the format trait (e.g. `{:#02x}` outputs "0x1"
  so width 2 has no effect; minimum is 4 for alternate hex/octal/binary)

## Examples

```rust
println!("{:.}", 1.0);

println!("not padded: {:5}", format_args!("..."));

// width 2 has no effect for alternate hex (outputs "0x1")
format!("{:#02x}", 1_u8);
```
Use instead:
```rust
println!("{}", 1.0);

println!("not padded: {}", format_args!("..."));
// OR
println!("padded: {:5}", format!("..."));

format!("{:#04x}", 1_u8);  // width 4 for two-digit zero-padded hex
```

[formatting parameters]: https://doc.rust-lang.org/std/fmt/index.html#formatting-parameters

## Further Reading

* [Clippy - unused_format_specs](https://clippy.rust-lang.org/stable/index.html#unused_format_specs)

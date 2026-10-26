Pattern: `Debug` formatting of `Path` or `OsStr`

Issue: -

## Description

Rust doesn't guarantee what `Debug` formatting looks like, and it could
change in the future. `OsStr`s and `Path`s can be `Display` formatted
using their `display` methods.

Furthermore, with `Debug` formatting, certain characters are escaped.
Thus, a `Debug` formatted `Path` is less likely to be clickable.

## What it does

Checks for `Debug` formatting (`{:?}`) applied to an `OsStr` or `Path`.

This includes:
- Format specifiers on `format_args!()` (width, precision have no effect)
- Format width too small for the format trait (e.g. `{:#02x}` outputs "0x1"
  so width 2 has no effect; minimum is 4 for alternate hex/octal/binary)

## Examples

Example of **incorrect** code:

```rust
let path = Path::new("...");
println!("The path is {:?}", path);
```

Example of **correct** code:

```rust
let path = Path::new("…");
println!("The path is {}", path.display());
```

## Further Reading

* [Clippy - unnecessary_debug_formatting](https://clippy.rust-lang.org/stable/index.html#unnecessary_debug_formatting)

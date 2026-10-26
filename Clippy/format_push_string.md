Pattern: Appending `format!` result to `String`

Issue: -

## Description

Introduces an extra, avoidable heap allocation.

## What it does

Detects cases where the result of a `format!` call is
appended to an existing `String`.

## Examples

Example of **incorrect** code:

```rust
let mut s = String::new();
s += &format!("0x{:X}", 1024);
s.push_str(&format!("0x{:X}", 1024));
```

Example of **correct** code:

```rust
use std::fmt::Write as _; // import without risk of name clashing

let mut s = String::new();
let _ = write!(s, "0x{:X}", 1024);
```

## Known problems

`format!` returns a `String` but `write!` returns a `Result`.
Thus you are forced to ignore the `Err` variant to achieve the same API.

While using `write!` in the suggested way should never fail, this isn't necessarily clear to the programmer.

## Further Reading

* [Clippy - format_push_string](https://clippy.rust-lang.org/stable/index.html#format_push_string)

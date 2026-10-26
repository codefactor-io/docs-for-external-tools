Pattern: Collecting `format!` results into `String`

Issue: -

## Description

This allocates a new string for every element in the iterator.
This can be done more efficiently by creating the `String` once and appending to it in `Iterator::fold`,
using either the `write!` macro which supports exactly the same syntax as the `format!` macro,
or concatenating with `+` in case the iterator yields `&str`/`String`.

Note also that `write!`-ing into a `String` can never fail, despite the return type of `write!` being `std::fmt::Result`,
so it can be safely ignored or unwrapped.

## What it does

Checks for usage of `.map(|_| format!(..)).collect::<String>()`.

## Examples

Example of **incorrect** code:

```rust
fn hex_encode(bytes: &[u8]) -> String {
    bytes.iter().map(|b| format!("{b:02X}")).collect()
}
```

Example of **correct** code:

```rust
use std::fmt::Write;
fn hex_encode(bytes: &[u8]) -> String {
    bytes.iter().fold(String::new(), |mut output, b| {
        let _ = write!(output, "{b:02X}");
        output
    })
}
```

## Further Reading

* [Clippy - format_collect](https://clippy.rust-lang.org/stable/index.html#format_collect)

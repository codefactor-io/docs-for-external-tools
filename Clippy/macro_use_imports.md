Pattern: Unnecessary `#[macro_use]` import

Issue: -

## Description

Since the Rust 2018 edition you can import
macro's directly, this is considered idiomatic.

## What it does

Checks for `#[macro_use] use...`.

## Examples

Example of **incorrect** code:

```rust
#[macro_use]
extern crate some_crate;

fn main() {
    some_macro!();
}
```

Example of **correct** code:

```rust
use some_crate::some_macro;

fn main() {
    some_macro!();
}
```

## Further Reading

* [Clippy - macro_use_imports](https://clippy.rust-lang.org/stable/index.html#macro_use_imports)

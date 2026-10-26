Pattern: Use of `Option<Option<T>>`

Issue: -

## Description

`Option<_>` represents an optional value. `Option<Option<_>>`
represents an optional value which itself wraps an optional. This is logically the
same thing as an optional value but has an unneeded extra level of wrapping.

If you have a case where `Some(Some(_))`, `Some(None)` and `None` are distinct cases,
consider a custom `enum` instead, with clear names for each case.

## What it does

Checks for usage of `Option<Option<_>>` in function signatures and type
definitions

## Examples

Example of **incorrect** code:

```rust
fn get_data() -> Option<Option<u32>> {
    None
}
```

Example of **correct** code:

```rust
pub enum Contents {
    Data(Vec<u8>), // Was Some(Some(Vec<u8>))
    NotYetFetched, // Was Some(None)
    None,          // Was None
}

fn get_data() -> Contents {
    Contents::None
}
```

## Further Reading

* [Clippy - option_option](https://clippy.rust-lang.org/stable/index.html#option_option)

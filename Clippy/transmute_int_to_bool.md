Pattern: Transmute from integer to `bool`

Issue: -

## Description

This might result in an invalid in-memory representation of a `bool`.

## What it does

Checks for transmutes from an integer to a `bool`.

## Examples

```rust
let x = 1_u8;
unsafe {
    let _: bool = std::mem::transmute(x); // where x: u8
}

// should be:
let _: bool = x != 0;
```

## Further Reading

* [Clippy - transmute_int_to_bool](https://clippy.rust-lang.org/stable/index.html#transmute_int_to_bool)

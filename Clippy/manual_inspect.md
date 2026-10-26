Pattern: Missing use of `inspect()`

Issue: -

## Description

`inspect` is both clearer in intent and shorter.

## What it does

Checks for uses of `map` which return the original item.

## Examples

Example of **incorrect** code:

```rust
let x = Some(0).map(|x| { println!("{x}"); x });
```

Example of **correct** code:

```rust
let x = Some(0).inspect(|x| println!("{x}"));
```

## Further Reading

* [Clippy - manual_inspect](https://clippy.rust-lang.org/stable/index.html#manual_inspect)

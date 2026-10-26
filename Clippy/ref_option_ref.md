Pattern: Use of `&Option<&T>`

Issue: -

## Description

Since `&` is Copy, it's useless to have a
reference on `Option<&T>`.

## What it does

Checks for usage of `&Option<&T>`.

## Examples

Example of **incorrect** code:

```rust
let x: &Option<&u32> = &Some(&0u32);
```

Example of **correct** code:

```rust
let x: Option<&u32> = Some(&0u32);
```

## Known problems

It may be irrelevant to use this lint on
public API code as it will make a breaking change to apply it.

## Further Reading

* [Clippy - ref_option_ref](https://clippy.rust-lang.org/stable/index.html#ref_option_ref)

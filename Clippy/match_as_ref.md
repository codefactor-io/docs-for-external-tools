Pattern: Missing use of `Option::as_ref()` or `as_mut()`

Issue: -

## Description

Using `as_ref()` or `as_mut()` instead is shorter.

## What it does

Checks for match which is used to add a reference to an
`Option` value.

## Examples

Example of **incorrect** code:

```rust
let x: Option<()> = None;

let r: Option<&()> = match x {
    None => None,
    Some(ref v) => Some(v),
};
```

Example of **correct** code:

```rust
let x: Option<()> = None;

let r: Option<&()> = x.as_ref();
```

## Further Reading

* [Clippy - match_as_ref](https://clippy.rust-lang.org/stable/index.html#match_as_ref)

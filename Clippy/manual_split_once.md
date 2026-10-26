Pattern: Missing use of `split_once()`

Issue: -

## Description

`split_once` is both clearer in intent and slightly more efficient.

## What it does

Checks for usage of `str::splitn(2, _)`

## Examples

Example of **incorrect** code:

```rust
let s = "key=value=add";
let (key, value) = s.splitn(2, '=').next_tuple()?;
let value = s.splitn(2, '=').nth(1)?;

let mut parts = s.splitn(2, '=');
let key = parts.next()?;
let value = parts.next()?;
```

Example of **correct** code:

```rust
let s = "key=value=add";
let (key, value) = s.split_once('=')?;
let value = s.split_once('=')?.1;

let (key, value) = s.split_once('=')?;
```

## Limitations

The multiple statement variant currently only detects `iter.next()?`/`iter.next().unwrap()`
in two separate `let` statements that immediately follow the `splitn()`

## Further Reading

* [Clippy - manual_split_once](https://clippy.rust-lang.org/stable/index.html#manual_split_once)

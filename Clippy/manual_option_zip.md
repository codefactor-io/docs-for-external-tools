Pattern: Missing use of `Option::zip()`

Issue: -

## Description

`Option::zip` is more concise and directly expresses the intent of
combining two `Option` values into a tuple.

## What it does

Checks for usage of `a.and_then(|a| b.map(|b| (a, b)))` which can be
more concisely expressed as `a.zip(b)`.

## Examples

Example of **incorrect** code:

```rust
let a: Option<i32> = Some(1);
let b: Option<i32> = Some(2);
let _ = a.and_then(|x| b.map(|y| (x, y)));
```

Example of **correct** code:

```rust
let a: Option<i32> = Some(1);
let b: Option<i32> = Some(2);
let _ = a.zip(b);
```

## Further Reading

* [Clippy - manual_option_zip](https://clippy.rust-lang.org/stable/index.html#manual_option_zip)

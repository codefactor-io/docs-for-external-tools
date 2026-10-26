Pattern: Missing use of `Option::ok_or()`

Issue: -

## Description

Concise code helps focusing on behavior instead of boilerplate.

## What it does

Finds patterns that reimplement `Option::ok_or`.

## Examples

Example of **incorrect** code:

```rust
let foo: Option<i32> = None;
foo.map_or(Err("error"), |v| Ok(v));
```

Example of **correct** code:

```rust
let foo: Option<i32> = None;
foo.ok_or("error");
```

## Further Reading

* [Clippy - manual_ok_or](https://clippy.rust-lang.org/stable/index.html#manual_ok_or)

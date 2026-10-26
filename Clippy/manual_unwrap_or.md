Pattern: Missing use of `unwrap_or()`

Issue: -

## Description

Concise code helps focusing on behavior instead of boilerplate.

## What it does

Finds patterns that reimplement `Option::unwrap_or` or `Result::unwrap_or`.

## Examples

Example of **incorrect** code:

```rust
let foo: Option<i32> = None;
match foo {
    Some(v) => v,
    None => 1,
};
```

Example of **correct** code:

```rust
let foo: Option<i32> = None;
foo.unwrap_or(1);
```

## Further Reading

* [Clippy - manual_unwrap_or](https://clippy.rust-lang.org/stable/index.html#manual_unwrap_or)

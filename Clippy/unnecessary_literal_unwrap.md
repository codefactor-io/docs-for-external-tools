Pattern: Unnecessary `unwrap()` on literal constructor

Issue: -

## Description

It is better to write the value directly without the indirection.

## What it does

Checks for `.unwrap()` related calls on `Result`s and `Option`s that are constructed.

## Examples

Example of **incorrect** code:

```rust
let val1 = Some(1).unwrap();
let val2 = Ok::<_, ()>(1).unwrap();
let val3 = Err::<(), _>(1).unwrap_err();
```

Example of **correct** code:

```rust
let val1 = 1;
let val2 = 1;
let val3 = 1;
```

## Further Reading

* [Clippy - unnecessary_literal_unwrap](https://clippy.rust-lang.org/stable/index.html#unnecessary_literal_unwrap)

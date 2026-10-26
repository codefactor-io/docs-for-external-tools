Pattern: Unnecessary cast

Issue: -

## Description

It's just unnecessary.

## What it does

Checks for casts to the same type, casts of int literals to integer
types, casts of float literals to float types, and casts between raw
pointers that don't change type or constness.

## Examples

Example of **incorrect** code:

```rust
let _ = 2i32 as i32;
let _ = 0.5 as f32;
```

Example of **correct** code:

```rust
let _ = 2_i32;
let _ = 0.5_f32;
```

## Known problems

When the expression on the left is a function call, the lint considers
the return type to be a type alias if it's aliased through a `use`
statement (like `use std::io::Result as IoResult`). It will not lint
such cases.

This check will only work on primitive types without any intermediate
references: raw pointers and trait objects may or may not work.

## Further Reading

* [Clippy - unnecessary_cast](https://clippy.rust-lang.org/stable/index.html#unnecessary_cast)

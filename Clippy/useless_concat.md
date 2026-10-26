Pattern: Useless `concat!` call

Issue: -

## Description

If there are less than 2 arguments, then calling the macro is doing nothing.

## What it does

Checks that the `concat!` macro has at least two arguments.

## Examples

Example of **incorrect** code:

```rust
let x = concat!("a");
```

Example of **correct** code:

```rust
let x = "a";
```

## Further Reading

* [Clippy - useless_concat](https://clippy.rust-lang.org/stable/index.html#useless_concat)

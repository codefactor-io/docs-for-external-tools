Pattern: Unnecessary `_` type in `let`

Issue: -

## Description

It adds noise, `: _` provides zero clarity or utility.

## What it does

Detects when a variable is declared with an explicit type of `_`.

## Examples

Example of **incorrect** code:

```rust
let my_number: _ = 1;
```

Example of **correct** code:

```rust
let my_number = 1;
```

## Further Reading

* [Clippy - let_with_type_underscore](https://clippy.rust-lang.org/stable/index.html#let_with_type_underscore)

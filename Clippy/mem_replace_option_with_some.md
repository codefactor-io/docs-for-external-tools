Pattern: Missing use of `Option::replace()`

Issue: -

## Description

`Option` already has the method `replace()` for
taking its current value (Some(…) or None) and replacing it with
`Some(…)`.

## What it does

Checks for `mem::replace()` on an `Option` with `Some(…)`.

## Examples

Example of **incorrect** code:

```rust
let mut an_option = Some(0);
let replaced = std::mem::replace(&mut an_option, Some(1));
```

Example of **correct** code:

```rust
let mut an_option = Some(0);
let taken = an_option.replace(1);
```

## Further Reading

* [Clippy - mem_replace_option_with_some](https://clippy.rust-lang.org/stable/index.html#mem_replace_option_with_some)

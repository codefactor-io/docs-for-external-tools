Pattern: Missing use of `Option::and_then()`

Issue: -

## Description

Readability, this can be written more concisely as
`_.and_then(_)`.

## What it does

Checks for usage of `_.map_or(None, _)`.

## Examples

Example of **incorrect** code:

```rust
opt.map_or(None, |a| Some(a + 1));
```

Example of **correct** code:

```rust
opt.and_then(|a| Some(a + 1));
```

## Known problems

The order of the arguments is not in execution order.

## Further Reading

* [Clippy - option_map_or_none](https://clippy.rust-lang.org/stable/index.html#option_map_or_none)

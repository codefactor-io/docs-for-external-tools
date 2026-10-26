Pattern: Use of `then_some().unwrap_or()`

Issue: -

## Description

This can be written more clearly with `if .. else ..`

## What it does

Checks for unnecessary method chains that can be simplified into `if .. else ..`.

## Examples

Example of **incorrect** code:

```rust
let x = true;
x.then_some("a").unwrap_or("b");
```

Example of **correct** code:

```rust
let x = true;
if x { "a" } else { "b" };
```

## Limitations

This lint currently only looks for usages of
`.{then, then_some}(..).{unwrap_or, unwrap_or_else, unwrap_or_default}(..)`, but will be expanded
to account for similar patterns.

## Further Reading

* [Clippy - obfuscated_if_else](https://clippy.rust-lang.org/stable/index.html#obfuscated_if_else)

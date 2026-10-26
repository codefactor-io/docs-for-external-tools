Pattern: Use of `skip_while().next()`

Issue: -

## Description

Readability, this can be written more concisely as
`_.find(!condition)`.

## What it does

Checks for usage of `_.skip_while(condition).next()`.

## Examples

Example of **incorrect** code:

```rust
vec.iter().skip_while(|x| **x == 0).next();
```

Example of **correct** code:

```rust
vec.iter().find(|x| **x != 0);
```

## Further Reading

* [Clippy - skip_while_next](https://clippy.rust-lang.org/stable/index.html#skip_while_next)

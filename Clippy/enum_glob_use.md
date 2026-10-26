Pattern: Glob import of enum variants

Issue: -

## Description

It is usually better style to use the prefixed name of
an enumeration variant, rather than importing variants.

## What it does

Checks for `use Enum::*`.

## Examples

Example of **incorrect** code:

```rust
use std::cmp::Ordering::*;

foo(Less);
```

Example of **correct** code:

```rust
use std::cmp::Ordering;

foo(Ordering::Less)
```

## Known problems

Old-style enumerations that prefix the variants are
still around.

## Further Reading

* [Clippy - enum_glob_use](https://clippy.rust-lang.org/stable/index.html#enum_glob_use)

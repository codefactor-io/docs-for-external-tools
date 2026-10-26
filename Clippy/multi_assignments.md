Pattern: Chained assignment

Issue: -

## Description

While this is in most cases already a type mismatch,
the result of an assignment being `()` can throw off people coming from languages like python or C,
where such assignments return a copy of the assigned value.

## What it does

Checks for nested assignments.

## Examples

Example of **incorrect** code:

```rust
a = b = 42;
```

Example of **correct** code:

```rust
b = 42;
a = b;
```

## Further Reading

* [Clippy - multi_assignments](https://clippy.rust-lang.org/stable/index.html#multi_assignments)

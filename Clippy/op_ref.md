Pattern: Unnecessary reference in `==` operand

Issue: -

## Description

It is more idiomatic to dereference the other argument.

## What it does

Checks for arguments to `==` which have their address
taken to satisfy a bound
and suggests to dereference the other argument instead

## Examples

Example of **incorrect** code:

```rust
&x == y
```

Example of **correct** code:

```rust
x == *y
```

## Further Reading

* [Clippy - op_ref](https://clippy.rust-lang.org/stable/index.html#op_ref)

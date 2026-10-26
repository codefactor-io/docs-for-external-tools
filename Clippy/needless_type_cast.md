Pattern: Binding always cast to another type

Issue: -

## Description

If a binding is always cast to a different type when used, it would be clearer
and more efficient to define it with the target type from the start.

## What it does

Checks for bindings (constants, statics, or let bindings) that are defined
with one numeric type but are consistently cast to a different type in all usages.

## Examples

Example of **incorrect** code:

```rust
const SIZE: u16 = 15;
let arr: [u8; SIZE as usize] = [0; SIZE as usize];
```

Example of **correct** code:

```rust
const SIZE: usize = 15;
let arr: [u8; SIZE] = [0; SIZE];
```

## Further Reading

* [Clippy - needless_type_cast](https://clippy.rust-lang.org/stable/index.html#needless_type_cast)

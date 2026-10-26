Pattern: Unnecessary struct update syntax

Issue: -

## Description

This will cost resources (because the base has to be
somewhere), and make the code less readable.

## What it does

Checks for needlessly including a base struct on update
when all fields are changed anyway.

This lint is not applied to structs marked with
[non_exhaustive](https://doc.rust-lang.org/reference/attributes/type_system.html).

## Examples

Example of **incorrect** code:

```rust
Point {
    x: 1,
    y: 1,
    z: 1,
    ..zero_point
};
```

Example of **correct** code:

```rust
Point {
    x: 1,
    y: 1,
    z: 1
};
```

## Further Reading

* [Clippy - needless_update](https://clippy.rust-lang.org/stable/index.html#needless_update)

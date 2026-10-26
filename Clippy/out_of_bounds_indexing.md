Pattern: Out of bounds constant indexing

Issue: -

## Description

This will always panic at runtime.

## What it does

Checks for out of bounds array indexing with a constant
index.

## Examples

Example of **incorrect** code:

```rust
let x = [1, 2, 3, 4];

x[9];
&x[2..9];
```

Example of **correct** code:

```rust
// Index within bounds

x[0];
x[3];
```

## Further Reading

* [Clippy - out_of_bounds_indexing](https://clippy.rust-lang.org/stable/index.html#out_of_bounds_indexing)

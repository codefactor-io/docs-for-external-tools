Pattern: Use of indexing or slicing

Issue: -

## Description

To avoid implicit panics from indexing and slicing.

There are “checked” alternatives which do not panic, and can be used with `unwrap()` to make
an explicit panic when it is desired.

## What it does

Checks for usage of indexing or slicing that may panic at runtime.

This lint does not report on indexing or slicing operations
that always panic, [out_of_bounds_indexing](#out_of_bounds_indexing) already
handles those cases.

## Examples

Example of **incorrect** code:

```rust
// Vector
let x = vec![0, 1, 2, 3];

x[2];
x[100];
&x[2..100];

// Array
let y = [0, 1, 2, 3];

let i = 10; // Could be a runtime value
let j = 20;
&y[i..j];
```

Example of **correct** code:

```rust
x.get(2);
x.get(100);
x.get(2..100);

let i = 10;
let j = 20;
y.get(i..j);
```

## Limitations

This lint does not check for the usage of indexing or slicing on strings. These are covered
by the more specific `string_slice` lint.

## Further Reading

* [Clippy - indexing_slicing](https://clippy.rust-lang.org/stable/index.html#indexing_slicing)

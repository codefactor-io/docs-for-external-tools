Pattern: `push()` right after `Vec` creation

Issue: -

## Description

The `vec![]` macro is both more performant and easier to read than
multiple `push` calls.

## What it does

Checks for calls to `push` immediately after creating a new `Vec`.

If the `Vec` is created using `with_capacity` this will only lint if the capacity is a
constant and the number of pushes is greater than or equal to the initial capacity.

If the `Vec` is extended after the initial sequence of pushes and it was default initialized
then this will only lint after there were at least four pushes. This number may change in
the future.

## Examples

Example of **incorrect** code:

```rust
let mut v = Vec::new();
v.push(0);
v.push(1);
v.push(2);
```

Example of **correct** code:

```rust
let v = vec![0, 1, 2];
```

## Further Reading

* [Clippy - vec_init_then_push](https://clippy.rust-lang.org/stable/index.html#vec_init_then_push)

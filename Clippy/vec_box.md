Pattern: Use of `Vec<Box<T>>` with sized `T`

Issue: -

## Description

`Vec` already keeps its contents in a separate area on
the heap. So if you `Box` its contents, you just add another level of indirection.

## What it does

Checks for usage of `Vec<Box<T>>` where T: Sized anywhere in the code.
Check the [Box documentation](https://doc.rust-lang.org/std/boxed/index.html) for more information.

## Examples

Example of **incorrect** code:

```rust
struct X {
    values: Vec<Box<i32>>,
}
```

Example of **correct** code:

```rust
struct X {
    values: Vec<i32>,
}
```

## Further Reading

* [Clippy - vec_box](https://clippy.rust-lang.org/stable/index.html#vec_box)

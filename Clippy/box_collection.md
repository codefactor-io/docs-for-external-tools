Pattern: Unnecessary `Box` around collection

Issue: -

## Description

Collections already keeps their contents in a separate area on
the heap. So if you `Box` them, you just add another level of indirection
without any benefit whatsoever.

## What it does

Checks for usage of `Box<T>` where T is a collection such as Vec anywhere in the code.
Check the [Box documentation](https://doc.rust-lang.org/std/boxed/index.html) for more information.

## Examples

Example of **incorrect** code:

```rust
struct X {
    values: Box<Vec<Foo>>,
}
```

Example of **correct** code:

```rust
struct X {
    values: Vec<Foo>,
}
```

## Further Reading

* [Clippy - box_collection](https://clippy.rust-lang.org/stable/index.html#box_collection)

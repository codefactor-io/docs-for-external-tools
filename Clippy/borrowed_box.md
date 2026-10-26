Pattern: Use of `&Box<T>`

Issue: -

## Description

A `&Box<T>` parameter requires the function caller to box `T` first before passing it to a function.
Using `&T` defines a concrete type for the parameter and generalizes the function, this would also
auto-deref to `&T` at the function call site if passed a `&Box<T>`.

## What it does

Checks for usage of `&Box<T>` anywhere in the code.
Check the [Box documentation](https://doc.rust-lang.org/std/boxed/index.html) for more information.

## Examples

Example of **incorrect** code:

```rust
fn foo(bar: &Box<T>) { ... }
```

Example of **correct** code:

```rust
fn foo(bar: &T) { ... }
```

## Further Reading

* [Clippy - borrowed_box](https://clippy.rust-lang.org/stable/index.html#borrowed_box)

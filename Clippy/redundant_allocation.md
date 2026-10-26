Pattern: Redundant allocation

Issue: -

## Description

Expressions such as `Rc<&T>`, `Rc<Rc<T>>`, `Rc<Arc<T>>`, `Rc<Box<T>>`, `Arc<&T>`, `Arc<Rc<T>>`,
`Arc<Arc<T>>`, `Arc<Box<T>>`, `Box<&T>`, `Box<Rc<T>>`, `Box<Arc<T>>`, `Box<Box<T>>`, add an unnecessary level of indirection.

## What it does

Checks for usage of redundant allocations anywhere in the code.

## Examples

Example of **incorrect** code:

```rust
fn foo(bar: Rc<&usize>) {}
```

Example of **correct** code:

```rust
fn foo(bar: &usize) {}
```

## Further Reading

* [Clippy - redundant_allocation](https://clippy.rust-lang.org/stable/index.html#redundant_allocation)

Pattern: Method-style `clone()` on ref-counted pointer

Issue: -

## Description

Calling `.clone()` on an `Rc`, `Arc`, or `Weak`
can obscure the fact that only the pointer is being cloned, not the underlying
data.

## What it does

Checks for usage of `.clone()` on a ref-counted pointer,
(`Rc`, `Arc`, `rc::Weak`, or `sync::Weak`), and suggests calling Clone via unified
function syntax instead (e.g., `Rc::clone(foo)`).

## Examples

Example of **incorrect** code:

```rust
let x = Rc::new(1);

x.clone();
```

Example of **correct** code:

```rust
Rc::clone(&x);
```

## Further Reading

* [Clippy - clone_on_ref_ptr](https://clippy.rust-lang.org/stable/index.html#clone_on_ref_ptr)

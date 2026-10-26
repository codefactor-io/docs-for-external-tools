Pattern: Use of `Rc` or `Arc` with buffer type

Issue: -

## Description

Expressions such as `Rc<String>` usually have no advantage over `Rc<str>`, since
it is larger and involves an extra level of indirection, and doesn't implement `Borrow<str>`.

While mutating a buffer type would still be possible with `Rc::get_mut()`, it only
works if there are no additional references yet, which usually defeats the purpose of
enclosing it in a shared ownership type. Instead, additionally wrapping the inner
type with an interior mutable container (such as `RefCell` or `Mutex`) would normally
be used.

## What it does

Checks for `Rc<T>` and `Arc<T>` when `T` is a mutable buffer type such as `String` or `Vec`.

## Examples

Example of **incorrect** code:

```rust
fn foo(interned: Rc<String>) { ... }
```

Example of **correct** code:

```rust
fn foo(interned: Rc<str>) { ... }
```

## Known problems

This pattern can be desirable to avoid the overhead of a `RefCell` or `Mutex` for
cases where mutation only happens before there are any additional references.

## Further Reading

* [Clippy - rc_buffer](https://clippy.rust-lang.org/stable/index.html#rc_buffer)

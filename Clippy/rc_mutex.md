Pattern: Use of `Rc<Mutex<T>>`

Issue: -

## Description

`Rc` is used in single thread and `Mutex` is used in multi thread.
Consider using `Rc<RefCell<T>>` in single thread or `Arc<Mutex<T>>` in multi thread.

## What it does

Checks for `Rc<Mutex<T>>`.

## Examples

Example of **incorrect** code:

```rust
use std::rc::Rc;
use std::sync::Mutex;
fn foo(interned: Rc<Mutex<i32>>) { ... }
```

Example of **correct** code:

```rust
use std::rc::Rc;
use std::cell::RefCell
fn foo(interned: Rc<RefCell<i32>>) { ... }
```

## Known problems

Sometimes combining generic types can lead to the requirement that a
type use Rc in conjunction with Mutex. We must consider those cases false positives, but
alas they are quite hard to rule out. Luckily they are also rare.

## Further Reading

* [Clippy - rc_mutex](https://clippy.rust-lang.org/stable/index.html#rc_mutex)

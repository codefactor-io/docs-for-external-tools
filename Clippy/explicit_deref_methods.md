Pattern: Explicit `deref()` or `deref_mut()` call

Issue: -

## Description

Dereferencing by `&*x` or `&mut *x` is clearer and more concise,
when not part of a method chain.

## What it does

Checks for explicit `deref()` or `deref_mut()` method calls.

Doesn't lint inside the implementation of the `Deref` or `DerefMut` traits.

## Examples

```rust
use std::ops::Deref;
let a: &mut String = &mut String::from("foo");
let b: &str = a.deref();
```

Use instead:
```rust
let a: &mut String = &mut String::from("foo");
let b = &*a;
```

This lint excludes all of:
```rust
let _ = d.unwrap().deref();
let _ = Foo::deref(&foo);
let _ = <Foo as Deref>::deref(&foo);
```

## Further Reading

* [Clippy - explicit_deref_methods](https://clippy.rust-lang.org/stable/index.html#explicit_deref_methods)

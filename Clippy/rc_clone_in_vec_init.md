Pattern: Reference-counted pointer in `vec![elem; len]`

Issue: -

## Description

This will create `elem` once and clone it `len` times - doing so with `Arc`/`Rc`/`Weak`
is a bit misleading, as it will create references to the same pointer, rather
than different instances.

## What it does

Checks for reference-counted pointers (`Arc`, `Rc`, `rc::Weak`, and `sync::Weak`)
in `vec![elem; len]`

## Examples

Example of **incorrect** code:

```rust
let v = vec![std::sync::Arc::new("some data".to_string()); 100];
// or
let v = vec![std::rc::Rc::new("some data".to_string()); 100];
```

Example of **correct** code:

```rust
// Initialize each value separately:
let mut data = Vec::with_capacity(100);
for _ in 0..100 {
    data.push(std::rc::Rc::new("some data".to_string()));
}

// Or if you want clones of the same reference,
// Create the reference beforehand to clarify that
// it should be cloned for each value
let data = std::rc::Rc::new("some data".to_string());
let v = vec![data; 100];
```

## Further Reading

* [Clippy - rc_clone_in_vec_init](https://clippy.rust-lang.org/stable/index.html#rc_clone_in_vec_init)

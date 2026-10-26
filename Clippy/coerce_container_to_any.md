Pattern: Unintended coercion to `&dyn Any`

Issue: -

## Description

The intention is usually to get a reference to the `dyn Any` the value dereferences to,
rather than coercing a reference to the container itself to `&dyn Any`.

## What it does

Protects against unintended coercion of references to container types to `&dyn Any` when the
container type dereferences to a `dyn Any` which could be directly referenced instead.

## Examples

Because `Box<dyn Any>` itself implements `Any`, `&Box<dyn Any>`
can be coerced to an `&dyn Any` which refers to *the `Box` itself*, rather than the
inner `dyn Any`.
```rust
let x: Box<dyn Any> = Box::new(0u32);
let dyn_any_of_box: &dyn Any = &x;

// Fails as we have a &dyn Any to the Box, not the u32
assert_eq!(dyn_any_of_box.downcast_ref::<u32>(), None);
```
Use instead:
```rust
let x: Box<dyn Any> = Box::new(0u32);
let dyn_any_of_u32: &dyn Any = &*x;

// Succeeds since we have a &dyn Any to the inner u32!
assert_eq!(dyn_any_of_u32.downcast_ref::<u32>(), Some(&0u32));
```

## Further Reading

* [Clippy - coerce_container_to_any](https://clippy.rust-lang.org/stable/index.html#coerce_container_to_any)

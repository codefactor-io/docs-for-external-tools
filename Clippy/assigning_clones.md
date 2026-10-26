Pattern: Missing use of `clone_from()` or `clone_into()`

Issue: -

## Description

Custom `Clone::clone_from()` or `ToOwned::clone_into` implementations allow the objects
to share resources and therefore avoid allocations.

## What it does

Checks for code like `foo = bar.clone();`

## Examples

Example of **incorrect** code:

```rust
struct Thing;

impl Clone for Thing {
    fn clone(&self) -> Self { todo!() }
    fn clone_from(&mut self, other: &Self) { todo!() }
}

pub fn assign_to_ref(a: &mut Thing, b: Thing) {
    *a = b.clone();
}
```

Example of **correct** code:

```rust
struct Thing;

impl Clone for Thing {
    fn clone(&self) -> Self { todo!() }
    fn clone_from(&mut self, other: &Self) { todo!() }
}

pub fn assign_to_ref(a: &mut Thing, b: Thing) {
    a.clone_from(&b);
}
```

## Further Reading

* [Clippy - assigning_clones](https://clippy.rust-lang.org/stable/index.html#assigning_clones)

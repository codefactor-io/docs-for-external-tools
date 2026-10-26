Pattern: Generic bounds in multiple locations

Issue: -

## Description

It can be confusing for developers when seeing bounds for a generic in multiple places.

## What it does

Check if a generic is defined both in the bound predicate and in the `where` clause.

## Examples

Example of **incorrect** code:

```rust
fn ty<F: std::fmt::Debug>(a: F)
where
    F: Sized,
{}
```

Example of **correct** code:

```rust
fn ty<F>(a: F)
where
    F: Sized + std::fmt::Debug,
{}
```

## Further Reading

* [Clippy - multiple_bound_locations](https://clippy.rust-lang.org/stable/index.html#multiple_bound_locations)

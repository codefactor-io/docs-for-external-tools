Pattern: Redundant implied bound in `impl Trait`

Issue: -

## Description

Specifying more bounds than necessary adds needless complexity for the reader.

## What it does

Looks for bounds in `impl Trait` in return position that are implied by other bounds.
This can happen when a trait is specified that another trait already has as a supertrait
(e.g. `fn() -> impl Deref + DerefMut<Target = i32>` has an unnecessary `Deref` bound,
because `Deref` is a supertrait of `DerefMut`)

## Examples

Example of **incorrect** code:

```rust
fn f() -> impl Deref<Target = i32> + DerefMut<Target = i32> {
//             ^^^^^^^^^^^^^^^^^^^ unnecessary bound, already implied by the `DerefMut` trait bound
    Box::new(123)
}
```

Example of **correct** code:

```rust
fn f() -> impl DerefMut<Target = i32> {
    Box::new(123)
}
```

## Limitations

This lint does not check for implied bounds transitively. Meaning that
it doesn't check for implied bounds from supertraits of supertraits
(e.g. `trait A {} trait B: A {} trait C: B {}`, then having an `fn() -> impl A + C`)

## Further Reading

* [Clippy - implied_bounds_in_impls](https://clippy.rust-lang.org/stable/index.html#implied_bounds_in_impls)

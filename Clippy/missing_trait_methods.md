Pattern: Trait impl relying on default method

Issue: -

## Description

To ensure that a certain implementation implements every method; for example,
a wrapper type where every method should delegate to the corresponding method of
the inner type's implementation.

This lint should typically be enabled on a specific trait `impl` item
rather than globally.

## What it does

Checks if a provided method is used implicitly by a trait
implementation.

## Examples

Example of **incorrect** code:

```rust
trait Trait {
    fn required();

    fn provided() {}
}

#[warn(clippy::missing_trait_methods)]
impl Trait for Type {
    fn required() { /* ... */ }
}
```

Example of **correct** code:

```rust
trait Trait {
    fn required();

    fn provided() {}
}

#[warn(clippy::missing_trait_methods)]
impl Trait for Type {
    fn required() { /* ... */ }

    fn provided() { /* ... */ }
}
```

## Further Reading

* [Clippy - missing_trait_methods](https://clippy.rust-lang.org/stable/index.html#missing_trait_methods)

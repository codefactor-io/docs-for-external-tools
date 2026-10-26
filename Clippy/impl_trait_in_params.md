Pattern: Use of `impl Trait` in function parameters

Issue: -

## Description

Turbofish syntax (`::<>`) cannot be used to specify the type of an `impl Trait` parameter,
making `impl Trait` less powerful. Readability may also be a factor.

## What it does

Lints when `impl Trait` is being used in a function's parameters.

## Examples

Example of **incorrect** code:

```rust
trait MyTrait {}
fn foo(a: impl MyTrait) {
	// [...]
}
```

Example of **correct** code:

```rust
trait MyTrait {}
fn foo<T: MyTrait>(a: T) {
	// [...]
}
```

## Further Reading

* [Clippy - impl_trait_in_params](https://clippy.rust-lang.org/stable/index.html#impl_trait_in_params)

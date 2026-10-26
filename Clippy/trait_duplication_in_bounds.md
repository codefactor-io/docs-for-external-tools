Pattern: Duplicate trait bounds

Issue: -

## Description

Duplicate bounds makes the code
less readable than specifying them only once.

## What it does

Checks for cases where generics or trait objects are being used and multiple
syntax specifications for trait bounds are used simultaneously.

## Examples

```rust
fn func<T: Clone + Default>(arg: T) where T: Clone + Default {}
```

Use instead:
```rust
fn func<T: Clone + Default>(arg: T) {}

// or

fn func<T>(arg: T) where T: Clone + Default {}
```

```rust
fn foo<T: Default + Default>(bar: T) {}
```
Use instead:
```rust
fn foo<T: Default>(bar: T) {}
```

```rust
fn foo<T>(bar: T) where T: Default + Default {}
```
Use instead:
```rust
fn foo<T>(bar: T) where T: Default {}
```

## Further Reading

* [Clippy - trait_duplication_in_bounds](https://clippy.rust-lang.org/stable/index.html#trait_duplication_in_bounds)

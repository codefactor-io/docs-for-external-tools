Pattern: Reference to uninhabited type

Issue: -

## Description

Dereferencing a reference to an uninhabited type would create
an instance of such a type, which cannot exist. This constitutes
undefined behaviour. Such a reference could have been created
by `unsafe` code.

## What it does

It detects references to uninhabited types, such as `!` and
warns when those are either dereferenced or returned from a function.

## Examples

The following function can return a reference to an uninhabited type
(`Infallible`) because it uses `unsafe` code to create it. However,
the user of such a function could dereference the return value and
trigger an undefined behavior from safe code.

```rust
fn create_ref() -> &'static std::convert::Infallible {
    unsafe { std::mem::transmute(&()) }
}
```

## Further Reading

* [Clippy - uninhabited_references](https://clippy.rust-lang.org/stable/index.html#uninhabited_references)

Pattern: Unnecessary `default()` on unit struct

Issue: -

## Description

This adds code complexity and an unnecessary function call.

## What it does

Checks for construction on unit struct using `default`.

## Examples

Example of **incorrect** code:

```rust
#[derive(Default)]
struct S<T> {
    _marker: PhantomData<T>
}

let _: S<i32> = S {
    _marker: PhantomData::default()
};
```

Example of **correct** code:

```rust
struct S<T> {
    _marker: PhantomData<T>
}

let _: S<i32> = S {
    _marker: PhantomData
};
```

## Further Reading

* [Clippy - default_constructed_unit_structs](https://clippy.rust-lang.org/stable/index.html#default_constructed_unit_structs)

Pattern: Transmute with undefined representation

Issue: -

## Description

The results of such a transmute are not defined.

## What it does

Checks for transmutes between types which do not have a representation defined relative to
each other.

## Examples

Example of **incorrect** code:

```rust
struct Foo<T>(u32, T);
let _ = unsafe { core::mem::transmute::<Foo<u32>, Foo<i32>>(Foo(0u32, 0u32)) };
```

Example of **correct** code:

```rust
#[repr(C)]
struct Foo<T>(u32, T);
let _ = unsafe { core::mem::transmute::<Foo<u32>, Foo<i32>>(Foo(0u32, 0u32)) };
```

## Known problems

This lint has had multiple problems in the past and was moved to `nursery`. See issue
[#8496](https://github.com/rust-lang/rust-clippy/issues/8496) for more details.

## Further Reading

* [Clippy - transmute_undefined_repr](https://clippy.rust-lang.org/stable/index.html#transmute_undefined_repr)

Pattern: `type_id()` on boxed trait object

Issue: -

## Description

This almost certainly does not do what the user expects and can lead to subtle bugs.
Calling `.type_id()` on a `Box<dyn Trait>` returns a fixed `TypeId` of the `Box` itself,
rather than returning the `TypeId` of the underlying type behind the trait object.

For `Box<dyn Any>` specifically (and trait objects that have `Any` as its supertrait),
this lint will provide a suggestion, which is to dereference the receiver explicitly
to go from `Box<dyn Any>` to `dyn Any`.
This makes sure that `.type_id()` resolves to a dynamic call on the trait object
and not on the box.

If the fixed `TypeId` of the `Box` is the intended behavior, it's better to be explicit about it
and write `TypeId::of::<Box<dyn Trait>>()`:
this makes it clear that a fixed `TypeId` is returned and not the `TypeId` of the implementor.

## What it does

Looks for calls to `.type_id()` on a `Box<dyn _>`.

## Examples

Example of **incorrect** code:

```rust
use std::any::{Any, TypeId};

let any_box: Box<dyn Any> = Box::new(42_i32);
assert_eq!(any_box.type_id(), TypeId::of::<i32>()); // ⚠️ this fails!
```

Example of **correct** code:

```rust
use std::any::{Any, TypeId};

let any_box: Box<dyn Any> = Box::new(42_i32);
assert_eq!((*any_box).type_id(), TypeId::of::<i32>());
//          ^ dereference first, to call `type_id` on `dyn Any`
```

## Further Reading

* [Clippy - type_id_on_box](https://clippy.rust-lang.org/stable/index.html#type_id_on_box)

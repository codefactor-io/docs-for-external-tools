Pattern: Transmute between incompatible collections

Issue: -

## Description

This is undefined behavior.

## What it does

Checks for transmutes between collections whose
types have different ABI, size or alignment.

## Examples

```rust
// different size, therefore likely out-of-bounds memory access
// You absolutely do not want this in your code!
unsafe {
    std::mem::transmute::<_, Vec<u32>>(vec![2_u16])
};
```

You must always iterate, map and collect the values:

```rust
vec![2_u16].into_iter().map(u32::from).collect::<Vec<_>>();
```

## Known problems

Currently, we cannot know whether a type is a
collection, so we just lint the ones that come with `std`.

## Further Reading

* [Clippy - unsound_collection_transmute](https://clippy.rust-lang.org/stable/index.html#unsound_collection_transmute)

Pattern: Tuple struct initialized with numbered fields

Issue: -

## Description

This may be confusing to the uninitiated and adds no
benefit as opposed to tuple initializers

## What it does

Checks for tuple structs initialized with field syntax.
It will however not lint if a base initializer is present.
The lint will also ignore code in macros.

## Examples

```rust
struct TupleStruct(u8, u16);

let _ = TupleStruct {
    0: 1,
    1: 23,
};

// should be written as
let base = TupleStruct(1, 23);

// This is OK however
let _ = TupleStruct { 0: 42, ..base };
```

## Further Reading

* [Clippy - init_numbered_fields](https://clippy.rust-lang.org/stable/index.html#init_numbered_fields)

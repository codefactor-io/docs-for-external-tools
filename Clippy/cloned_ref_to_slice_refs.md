Pattern: Missing use of `slice::from_ref()`

Issue: -

## Description

A reference does not need to be owned in order to be used as a slice.

## What it does

Checks for slice references with cloned references such as `&[f.clone()]`.

## Examples

Example of **incorrect** code:

```rust
let data = 10;
let data_ref = &data;
take_slice(&[data_ref.clone()]);
```

Example of **correct** code:

```rust
use std::slice;
let data = 10;
let data_ref = &data;
take_slice(slice::from_ref(data_ref));
```

## Known problems

This lint does not know whether or not a clone implementation has side effects.

## Further Reading

* [Clippy - cloned_ref_to_slice_refs](https://clippy.rust-lang.org/stable/index.html#cloned_ref_to_slice_refs)

Pattern: Slow vector initialization

Issue: -

## Description

These structures are non-idiomatic and less efficient than simply using
`vec![0; len]`.

Specifically, for `vec![0; len]`, the compiler can use a specialized type of allocation
that also zero-initializes the allocated memory in the same call
(see: [alloc_zeroed](https://doc.rust-lang.org/stable/std/alloc/trait.GlobalAlloc.html#method.alloc_zeroed)).

Writing `Vec::new()` followed by `vec.resize(len, 0)` is suboptimal because,
while it does do the same number of allocations,
it involves two operations for allocating and initializing.
The `resize` call first allocates memory (since `Vec::new()` did not), and only *then* zero-initializes it.

## What it does

Checks slow zero-filled vector initialization

## Examples

Example of **incorrect** code:

```rust
let mut vec1 = Vec::new();
vec1.resize(len, 0);

let mut vec2 = Vec::with_capacity(len);
vec2.resize(len, 0);

let mut vec3 = Vec::with_capacity(len);
vec3.extend(repeat(0).take(len));
```

Example of **correct** code:

```rust
let mut vec1 = vec![0; len];
let mut vec2 = vec![0; len];
let mut vec3 = vec![0; len];
```

## Further Reading

* [Clippy - slow_vector_initialization](https://clippy.rust-lang.org/stable/index.html#slow_vector_initialization)

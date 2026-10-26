Pattern: Repeated indexing without length `assert!`

Issue: -

## Description

In the general case where the compiler does not have a lot of information
about the length of a slice, indexing it repeatedly will generate a bounds check
for every single index.

Asserting that the length of the slice is at least as large as the largest value
to index beforehand gives the compiler enough information to elide the bounds checks,
effectively reducing the number of bounds checks from however many times
the slice was indexed to just one (the assert).

## What it does

Checks for repeated slice indexing without asserting beforehand that the length
is greater than the largest index used to index into the slice.

## Examples

Example of **incorrect** code:

```rust
fn sum(v: &[u8]) -> u8 {
    // 4 bounds checks
    v[0] + v[1] + v[2] + v[3]
}
```

Example of **correct** code:

```rust
fn sum(v: &[u8]) -> u8 {
    assert!(v.len() > 3);
    // no bounds checks
    v[0] + v[1] + v[2] + v[3]
}
```

## Drawbacks

False positives. It is, in general, very difficult to predict how well
the optimizer will be able to elide bounds checks and it very much depends on
the surrounding code. For example, indexing into the slice yielded by the
[`slice::chunks_exact`](https://doc.rust-lang.org/stable/std/primitive.slice.html#method.chunks_exact)
iterator will likely have all of the bounds checks elided even without an assert
if the `chunk_size` is a constant.

Asserts are not tracked across function calls. Asserting the length of a slice
in a different function likely gives the optimizer enough information
about the length of a slice, but this lint will not detect that.

## Further Reading

* [Clippy - missing_asserts_for_indexing](https://clippy.rust-lang.org/stable/index.html#missing_asserts_for_indexing)

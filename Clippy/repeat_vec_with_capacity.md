Pattern: Repeated `Vec::with_capacity()` value

Issue: -

## Description

These constructs work by cloning the element, but cloning a `Vec<_>` does not
respect the old vector's capacity and effectively discards it.

This makes `iter::repeat(Vec::with_capacity(x))` especially suspicious because the user most certainly
expected that the yielded `Vec<_>` will have the requested capacity, otherwise one can simply write
`iter::repeat(Vec::new())` instead and it will have the same effect.

Similarly for `vec![x; n]`, the element `x` is cloned to fill the vec.
Unlike `iter::repeat` however, the vec repeat macro does not have to clone the value `n` times
but just `n - 1` times, because it can reuse the passed value for the last slot.
That means that the last `Vec<_>` gets the requested capacity but all other ones do not.

## What it does

Looks for patterns such as `vec![Vec::with_capacity(x); n]` or `iter::repeat(Vec::with_capacity(x))`.

## Examples

Example of **incorrect** code:

```rust

let _: Vec<Vec<u8>> = vec![Vec::with_capacity(42); 123];
let _: Vec<Vec<u8>> = iter::repeat(Vec::with_capacity(42)).take(123).collect();
```

Example of **correct** code:

```rust

let _: Vec<Vec<u8>> = iter::repeat_with(|| Vec::with_capacity(42)).take(123).collect();
//                                      ^^^ this closure executes 123 times
//                                          and the vecs will have the expected capacity
```

## Further Reading

* [Clippy - repeat_vec_with_capacity](https://clippy.rust-lang.org/stable/index.html#repeat_vec_with_capacity)

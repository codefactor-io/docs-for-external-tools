Pattern: Function that only maps `Option` argument

Issue: -

## Description

Taking and returning an `Option<T>` may require additional
`Some(_)` and `unwrap` if all you have is a `T`.

## What it does

Checks for functions with method calls to `.map(_)` on an arg
of type `Option` as the outermost expression.

## Examples

Example of **incorrect** code:

```rust
fn double(param: Option<u32>) -> Option<u32> {
    param.map(|x| x * 2)
}
```

Example of **correct** code:

```rust
fn double(param: u32) -> u32 {
    param * 2
}
```

## Further Reading

* [Clippy - single_option_map](https://clippy.rust-lang.org/stable/index.html#single_option_map)

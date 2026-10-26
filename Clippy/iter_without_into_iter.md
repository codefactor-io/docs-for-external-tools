Pattern: `iter()` method without `IntoIterator` impl

Issue: -

## Description

It's not bad, but having them is idiomatic and allows the type to be used in for loops directly
(`for val in &iter {}`), without having to first call `iter()` or `iter_mut()`.

## What it does

Looks for `iter` and `iter_mut` methods without an associated `IntoIterator for (&|&mut) Type` implementation.

## Examples

Example of **incorrect** code:

```rust
struct MySlice<'a>(&'a [u8]);
impl<'a> MySlice<'a> {
    pub fn iter(&self) -> std::slice::Iter<'a, u8> {
        self.0.iter()
    }
}
```

Example of **correct** code:

```rust
struct MySlice<'a>(&'a [u8]);
impl<'a> MySlice<'a> {
    pub fn iter(&self) -> std::slice::Iter<'a, u8> {
        self.0.iter()
    }
}
impl<'a> IntoIterator for &MySlice<'a> {
    type Item = &'a u8;
    type IntoIter = std::slice::Iter<'a, u8>;
    fn into_iter(self) -> Self::IntoIter {
        self.iter()
    }
}
```

## Limitations

This lint focuses on providing an idiomatic API. Therefore, it will only
lint on types which are accessible outside of the crate. For internal types,
the `IntoIterator` trait can be implemented on demand if it is actually needed.

## Further Reading

* [Clippy - iter_without_into_iter](https://clippy.rust-lang.org/stable/index.html#iter_without_into_iter)

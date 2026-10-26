Pattern: `IntoIterator` impl without `iter()` method

Issue: -

## Description

It's not bad, but having them is idiomatic and allows the type to be used in iterator chains
by just calling `.iter()`, instead of the more awkward `<&Type>::into_iter` or `(&val).into_iter()` syntax
in case of ambiguity with another `IntoIterator` impl.

## What it does

This is the opposite of the `iter_without_into_iter` lint.
It looks for `IntoIterator for (&|&mut) Type` implementations without an inherent `iter` or `iter_mut` method
on the type or on any of the types in its `Deref` chain.

## Examples

Example of **incorrect** code:

```rust
struct MySlice<'a>(&'a [u8]);
impl<'a> IntoIterator for &MySlice<'a> {
    type Item = &'a u8;
    type IntoIter = std::slice::Iter<'a, u8>;
    fn into_iter(self) -> Self::IntoIter {
        self.0.iter()
    }
}
```

Example of **correct** code:

```rust
struct MySlice<'a>(&'a [u8]);
impl<'a> MySlice<'a> {
    pub fn iter(&self) -> std::slice::Iter<'a, u8> {
        self.into_iter()
    }
}
impl<'a> IntoIterator for &MySlice<'a> {
    type Item = &'a u8;
    type IntoIter = std::slice::Iter<'a, u8>;
    fn into_iter(self) -> Self::IntoIter {
        self.0.iter()
    }
}
```

## Limitations

This lint focuses on providing an idiomatic API. Therefore, it will only
lint on types which are accessible outside of the crate. For internal types,
these methods can be added on demand if they are actually needed. Otherwise,
it would trigger the [`dead_code`] lint for the unused method.

[`dead_code`]: https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#dead-code

## Further Reading

* [Clippy - into_iter_without_iter](https://clippy.rust-lang.org/stable/index.html#into_iter_without_iter)

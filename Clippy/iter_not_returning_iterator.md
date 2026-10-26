Pattern: `iter()` method not returning `Iterator`

Issue: -

## Description

Methods named `iter` or `iter_mut` conventionally return an `Iterator`.

## What it does

Detects methods named `iter` or `iter_mut` that do not have a return type that implements `Iterator`.

## Examples

Example of **incorrect** code:

```rust
// `String` does not implement `Iterator`
struct Data {}
impl Data {
    fn iter(&self) -> String {
        todo!()
    }
}
```

Example of **correct** code:

```rust
use std::str::Chars;
struct Data {}
impl Data {
    fn iter(&self) -> Chars<'static> {
        todo!()
    }
}
```

## Further Reading

* [Clippy - iter_not_returning_iterator](https://clippy.rust-lang.org/stable/index.html#iter_not_returning_iterator)

Pattern: Useless `format!`

Issue: -

## Description

There is no point of doing that. `format!("foo")` can
be replaced by `"foo".to_owned()` if you really need a `String`. The even
worse `&format!("foo")` is often encountered in the wild. `format!("{}",
foo)` can be replaced by `foo.clone()` if `foo: String` or `foo.to_owned()`
if `foo: &str`.

## What it does

Checks for the use of `format!("string literal with no
argument")` and `format!("{}", foo)` where `foo` is a string.

## Examples

Example of **incorrect** code:

```rust
let foo = "foo";
format!("{}", foo);
```

Example of **correct** code:

```rust
let foo = "foo";
foo.to_owned();
```

## Further Reading

* [Clippy - useless_format](https://clippy.rust-lang.org/stable/index.html#useless_format)

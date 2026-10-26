Pattern: Unnecessary `Box<T>` return type

Issue: -

## Description

It's better to just return `T` in these cases. The caller may not need
the value to be boxed, and it's expensive to free the memory once the
`Box<T>` been dropped.

## What it does

Checks for a return type containing a `Box<T>` where `T` implements `Sized`

The lint ignores `Box<T>` where `T` is larger than `unnecessary_box_size`,
as returning a large `T` directly may be detrimental to performance.

## Examples

Example of **incorrect** code:

```rust
fn foo() -> Box<String> {
    Box::new(String::from("Hello, world!"))
}
```

Example of **correct** code:

```rust
fn foo() -> String {
    String::from("Hello, world!")
}
```

## Further Reading

* [Clippy - unnecessary_box_returns](https://clippy.rust-lang.org/stable/index.html#unnecessary_box_returns)

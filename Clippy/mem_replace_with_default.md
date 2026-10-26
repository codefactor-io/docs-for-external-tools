Pattern: `mem::replace()` with `T::default()`

Issue: -

## Description

`std::mem` module already has the method `take` to
take the current value and replace it with the default value of that type.

## What it does

Checks for `std::mem::replace` on a value of type
`T` with `T::default()`.

## Examples

Example of **incorrect** code:

```rust
let mut text = String::from("foo");
let replaced = std::mem::replace(&mut text, String::default());
```

Example of **correct** code:

```rust
let mut text = String::from("foo");
let taken = std::mem::take(&mut text);
```

## Further Reading

* [Clippy - mem_replace_with_default](https://clippy.rust-lang.org/stable/index.html#mem_replace_with_default)

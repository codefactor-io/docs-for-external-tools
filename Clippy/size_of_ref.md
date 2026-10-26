Pattern: Double reference in `size_of_val()`

Issue: -

## Description

Calling `size_of_val()` with a reference to a reference as the argument
yields the size of the reference-type, not the size of the value behind
the reference.

## What it does

Checks for calls to `size_of_val()` where the argument is
a reference to a reference.

## Examples

Example of **incorrect** code:

```rust
struct Foo {
    buffer: [u8],
}

impl Foo {
    fn size(&self) -> usize {
        // Note that `&self` as an argument is a `&&Foo`: Because `self`
        // is already a reference, `&self` is a double-reference.
        // The return value of `size_of_val()` therefore is the
        // size of the reference-type, not the size of `self`.
        size_of_val(&self)
    }
}
```

Example of **correct** code:

```rust
struct Foo {
    buffer: [u8],
}

impl Foo {
    fn size(&self) -> usize {
        // Correct
        size_of_val(self)
    }
}
```

## Further Reading

* [Clippy - size_of_ref](https://clippy.rust-lang.org/stable/index.html#size_of_ref)

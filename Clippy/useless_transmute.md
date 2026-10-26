Pattern: Useless transmute

Issue: -

## Description

Readability. The code tricks people into thinking that
something complex is going on.

## What it does

Checks for transmutes to the original type of the object
and transmutes that could be a cast.

## Examples

Example of **incorrect** code:

```rust
core::intrinsics::transmute(t); // where the result type is the same as `t`'s
```

## Further Reading

* [Clippy - useless_transmute](https://clippy.rust-lang.org/stable/index.html#useless_transmute)

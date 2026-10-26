Pattern: Conversion from `bool` to integer using `if`

Issue: -

## Description

Coercion or `from()` is another way to convert bool to a number.
Both methods are guaranteed to return 1 for true, and 0 for false.

See https://doc.rust-lang.org/std/primitive.bool.html#impl-From%3Cbool%3E

## What it does

Instead of using an if statement to convert a bool to an int,
this lint suggests using a `from()` function or an `as` coercion.

## Examples

```rust
if condition {
    1_i64
} else {
    0
};
```
Use instead:
```rust
i64::from(condition);
```
or
```rust
condition as i64;
```

## Further Reading

* [Clippy - bool_to_int_with_if](https://clippy.rust-lang.org/stable/index.html#bool_to_int_with_if)

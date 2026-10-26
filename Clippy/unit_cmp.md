Pattern: Unit value comparison

Issue: -

## Description

Unit is always equal to itself, and thus is just a
clumsily written constant. Mostly this happens when someone accidentally
adds semicolons at the end of the operands.

## What it does

Checks for comparisons to unit. This includes all binary
comparisons (like `==` and `<`) and asserts.

## Examples

```rust
if {
    foo();
} == {
    bar();
} {
    baz();
}
```
is equal to
```rust
{
    foo();
    bar();
    baz();
}
```

For asserts:
```rust
assert_eq!({ foo(); }, { bar(); });
```
will always succeed

## Further Reading

* [Clippy - unit_cmp](https://clippy.rust-lang.org/stable/index.html#unit_cmp)

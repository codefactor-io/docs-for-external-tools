Pattern: Argument passed by value but not consumed

Issue: -

## Description

Taking arguments by reference is more flexible and can
sometimes avoid
unnecessary allocations.

## What it does

Checks for functions taking arguments by value, but not
consuming them in its
body.

## Examples

Example of **incorrect** code:

```rust
fn foo(v: Vec<i32>) {
    assert_eq!(v.len(), 42);
}
```

Example of **correct** code:

```rust
fn foo(v: &[i32]) {
    assert_eq!(v.len(), 42);
}
```

## Known problems

* This lint suggests taking an argument by reference,
however sometimes it is better to let users decide the argument type
(by using `Borrow` trait, for example), depending on how the function is used.

## Further Reading

* [Clippy - needless_pass_by_value](https://clippy.rust-lang.org/stable/index.html#needless_pass_by_value)

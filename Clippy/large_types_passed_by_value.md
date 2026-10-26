Pattern: Large `Copy` type passed by value

Issue: -

## Description

Arguments passed by value might result in an unnecessary
shallow copy, taking up more space in the stack and requiring a call to
`memcpy`, which can be expensive.

## What it does

Checks for functions taking arguments by value, where
the argument type is `Copy` and large enough to be worth considering
passing by reference. Does not trigger if the function is being exported,
because that might induce API breakage, if the parameter is declared as mutable,
or if the argument is a `self`.

## Examples

Example of **incorrect** code:

```rust
#[derive(Clone, Copy)]
struct TooLarge([u8; 2048]);

fn foo(v: TooLarge) {}
```

Example of **correct** code:

```rust
fn foo(v: &TooLarge) {}
```

## Further Reading

* [Clippy - large_types_passed_by_value](https://clippy.rust-lang.org/stable/index.html#large_types_passed_by_value)

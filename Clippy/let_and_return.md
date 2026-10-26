Pattern: Unnecessary `let` before return

Issue: -

## Description

It is just extraneous code. Remove it to make your code
more rusty.

## What it does

Checks for `let`-bindings, which are subsequently
returned.

## Examples

```rust
fn foo() -> String {
    let x = String::new();
    x
}
```
instead, use
```rust
fn foo() -> String {
    String::new()
}
```

## Known problems

In the case of some temporaries, e.g. locks, eliding the variable binding could lead
to deadlocks. See [this issue](https://github.com/rust-lang/rust/issues/37612).
This could become relevant if the code is later changed to use the code that would have been
bound without first assigning it to a let-binding.

## Further Reading

* [Clippy - let_and_return](https://clippy.rust-lang.org/stable/index.html#let_and_return)

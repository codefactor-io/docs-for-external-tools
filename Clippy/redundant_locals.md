Pattern: Redundant redefinition of local binding

Issue: -

## Description

Redundant redefinitions of local bindings do not change behavior other than variable's lifetimes and are likely to be unintended.

These rebindings can be intentional to shorten the lifetimes of variables because they affect when the `Drop` implementation is called. Other than that, they do not affect your code's meaning but they _may_ affect `rustc`'s stack allocation.

## What it does

Checks for redundant redefinitions of local bindings.

## Examples

Example of **incorrect** code:

```rust
let a = 0;
let a = a;

fn foo(b: i32) {
    let b = b;
}
```

Example of **correct** code:

```rust
let a = 0;
// no redefinition with the same name

fn foo(b: i32) {
  // no redefinition with the same name
}
```

## Further Reading

* [Clippy - redundant_locals](https://clippy.rust-lang.org/stable/index.html#redundant_locals)

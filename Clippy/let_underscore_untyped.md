Pattern: Untyped `let _` binding

Issue: -

## Description

The `let _ = <expr>` expression ignores the value of `<expr>`, but will continue to do so even
if the type were to change, thus potentially introducing subtle bugs. By supplying a type
annotation, one will be forced to re-visit the decision to ignore the value in such cases.

## What it does

Checks for `let _ = <expr>` without a type annotation, and suggests to either provide one,
or remove the `let` keyword altogether.

## Examples

Example of **incorrect** code:

```rust
fn foo() -> Result<u32, ()> {
    Ok(123)
}
let _ = foo();
```

Example of **correct** code:

```rust
fn foo() -> Result<u32, ()> {
    Ok(123)
}
// Either provide a type annotation:
let _: Result<u32, ()> = foo();
// …or drop the let keyword:
_ = foo();
```

## Known problems

The `_ = <expr>` is not properly supported by some tools (e.g. IntelliJ) and may seem odd
to many developers. This lint also partially overlaps with the other `let_underscore_*`
lints.

## Further Reading

* [Clippy - let_underscore_untyped](https://clippy.rust-lang.org/stable/index.html#let_underscore_untyped)

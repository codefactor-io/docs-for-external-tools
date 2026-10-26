Pattern: Unnecessary borrow for generic argument

Issue: -

## Description

Suggests that the receiver of the expression borrows
the expression.

## What it does

Checks for borrow operations (`&`) that are used as a generic argument to a
function when the borrowed value could be used.

## Examples

Example of **incorrect** code:

```rust
fn f(_: impl AsRef<str>) {}

let x = "foo";
f(&x);
```

Example of **correct** code:

```rust
fn f(_: impl AsRef<str>) {}

let x = "foo";
f(x);
```

## Known problems

The lint cannot tell when the implementation of a trait
for `&T` and `T` do different things. Removing a borrow
in such a case can change the semantics of the code.

## Further Reading

* [Clippy - needless_borrows_for_generic_args](https://clippy.rust-lang.org/stable/index.html#needless_borrows_for_generic_args)

Pattern: Unnecessary borrow

Issue: -

## Description

Suggests that the receiver of the expression borrows
the expression.

## What it does

Checks for address of operations (`&`) that are going to
be dereferenced immediately by the compiler.

## Examples

Example of **incorrect** code:

```rust
fn fun(_a: &i32) {}

let x: &i32 = &&&&&&5;
fun(&x);
```

Example of **correct** code:

```rust
let x: &i32 = &5;
fun(x);
```

## Known problems

The lint cannot tell when the implementation of a trait
for `&T` and `T` do different things. Removing a borrow
in such a case can change the semantics of the code.

## Further Reading

* [Clippy - needless_borrow](https://clippy.rust-lang.org/stable/index.html#needless_borrow)

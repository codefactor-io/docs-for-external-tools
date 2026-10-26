Pattern: Eager evaluation of `transmute()`

Issue: -

## Description

Eager evaluation means that the `transmute` call is executed regardless of whether the condition is true or false.
This can introduce unsoundness and other subtle bugs.

## What it does

Checks for integer validity checks, followed by a transmute that is (incorrectly) evaluated
eagerly (e.g. using `bool::then_some`).

## Examples

Consider the following function which is meant to convert an unsigned integer to its enum equivalent via transmute.

```rust
#[repr(u8)]
enum Opcode {
    Add = 0,
    Sub = 1,
    Mul = 2,
    Div = 3
}

fn int_to_opcode(op: u8) -> Option<Opcode> {
    (op < 4).then_some(unsafe { std::mem::transmute(op) })
}
```
This may appear fine at first given that it checks that the `u8` is within the validity range of the enum,
*however* the transmute is evaluated eagerly, meaning that it executes even if `op >= 4`!

This makes the function unsound, because it is possible for the caller to cause undefined behavior
(creating an enum with an invalid bitpattern) entirely in safe code only by passing an incorrect value,
which is normally only a bug that is possible in unsafe code.

One possible way in which this can go wrong practically is that the compiler sees it as:
```rust
let temp: Foo = unsafe { std::mem::transmute(op) };
(0 < 4).then_some(temp)
```
and optimizes away the `(0 < 4)` check based on the assumption that since a `Foo` was created from `op` with the validity range `0..3`,
it is **impossible** for this condition to be false.

In short, it is possible for this function to be optimized in a way that makes it [never return `None`](https://godbolt.org/z/ocrcenevq),
even if passed the value `4`.

This can be avoided by instead using lazy evaluation. For the example above, this should be written:
```rust
fn int_to_opcode(op: u8) -> Option<Opcode> {
    (op < 4).then(|| unsafe { std::mem::transmute(op) })
             ^^^^ ^^ `bool::then` only executes the closure if the condition is true!
}
```

## Further Reading

* [Clippy - eager_transmute](https://clippy.rust-lang.org/stable/index.html#eager_transmute)

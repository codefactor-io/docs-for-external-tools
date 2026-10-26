Pattern: Arithmetic with possible overflow or panic

Issue: -

## Description

For integers, overflow will trigger a panic in debug builds or wrap the result in
release mode; division by zero will cause a panic in either mode. As a result, it is
desirable to explicitly call checked, wrapping or saturating arithmetic methods.

#### Example
```rust
// `n` can be any number, including `i32::MAX`.
fn foo(n: i32) -> i32 {
    n + 1
}
```

Third-party types can also overflow or present unwanted side-effects.

#### Example
```rust
use rust_decimal::Decimal;
let _n = Decimal::MAX + Decimal::MAX;
```

## What it does

Checks any kind of arithmetic operation of any type.

Operators like `+`, `-`, `*` or `<<` are usually capable of overflowing according to the [Rust
Reference](https://doc.rust-lang.org/reference/expressions/operator-expr.html#overflow),
or can panic (`/`, `%`).

Known safe built-in types like `Wrapping` or `Saturating`, floats, operations in constant
environments, allowed types and non-constant operations that won't overflow are ignored.

## Further Reading

* [Clippy - arithmetic_side_effects](https://clippy.rust-lang.org/stable/index.html#arithmetic_side_effects)

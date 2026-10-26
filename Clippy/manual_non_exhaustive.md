Pattern: Missing use of `#[non_exhaustive]`

Issue: -

## Description

Using the #[non_exhaustive] attribute expresses better the intent
and allows possible optimizations when applied to enums.

## What it does

Checks for manual implementations of the non-exhaustive pattern.

## Examples

Example of **incorrect** code:

```rust
struct S {
    pub a: i32,
    pub b: i32,
    _c: (),
}

enum E {
    A,
    B,
    #[doc(hidden)]
    _C,
}

struct T(pub i32, pub i32, ());
```

Example of **correct** code:

```rust
#[non_exhaustive]
struct S {
    pub a: i32,
    pub b: i32,
}

#[non_exhaustive]
enum E {
    A,
    B,
}

#[non_exhaustive]
struct T(pub i32, pub i32);
```

## Further Reading

* [Clippy - manual_non_exhaustive](https://clippy.rust-lang.org/stable/index.html#manual_non_exhaustive)

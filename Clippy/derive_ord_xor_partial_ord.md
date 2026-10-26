Pattern: Derived `Ord` with manual `PartialOrd`

Issue: -

## Description

The implementation of these traits must agree (for
example for use with `sort`) so it’s probably a bad idea to use a
default-generated `Ord` implementation with an explicitly defined
`PartialOrd`. In particular, the following must hold for any type
implementing `Ord`:

```text
k1.cmp(&k2) == k1.partial_cmp(&k2).unwrap()
```

## What it does

Lints against manual `PartialOrd` and `Ord` implementations for types with a derived `Ord`
or `PartialOrd` implementation.

## Examples

```rust
#[derive(Ord, PartialEq, Eq)]
struct Foo;

impl PartialOrd for Foo {
    ...
}
```
Use instead:
```rust
#[derive(PartialEq, Eq)]
struct Foo;

impl PartialOrd for Foo {
    fn partial_cmp(&self, other: &Foo) -> Option<Ordering> {
       Some(self.cmp(other))
    }
}

impl Ord for Foo {
    ...
}
```
or, if you don't need a custom ordering:
```rust
#[derive(Ord, PartialOrd, PartialEq, Eq)]
struct Foo;
```

## Further Reading

* [Clippy - derive_ord_xor_partial_ord](https://clippy.rust-lang.org/stable/index.html#derive_ord_xor_partial_ord)

Pattern: Redundant struct initialization from instance

Issue: -

## Description

Readability suffers from unnecessary struct building.

## What it does

Checks for initialization of an identical `struct` from another instance
of the type, either by copying a base without setting any field or by
moving all fields individually.

## Examples

```rust
struct S { s: String }

let a = S { s: String::from("Hello, world!") };
let b = S { ..a };
```
Use instead:
```rust
struct S { s: String }

let a = S { s: String::from("Hello, world!") };
let b = a;
```

The struct literal ``S { ..a }`` in the assignment to ``b`` could be replaced
with just ``a``.

## Known Problems

Has false positives when the base is a place expression that cannot be
moved out of, see [#10547](https://github.com/rust-lang/rust-clippy/issues/10547).

Empty structs are ignored by the lint.

## Further Reading

* [Clippy - unnecessary_struct_initialization](https://clippy.rust-lang.org/stable/index.html#unnecessary_struct_initialization)

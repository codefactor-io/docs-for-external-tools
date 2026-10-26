Pattern: Inconsistent field order in struct constructor

Issue: -

## Description

Since the order of fields in a constructor doesn't affect the
resulted instance as the below example indicates,

```rust
#[derive(Debug, PartialEq, Eq)]
struct Foo {
    x: i32,
    y: i32,
}
let x = 1;
let y = 2;

// This assertion never fails:
assert_eq!(Foo { x, y }, Foo { y, x });
```

inconsistent order can be confusing and decreases readability and consistency.

## What it does

Checks for struct constructors where the order of the field
init in the constructor is inconsistent with the order in the
struct definition.

## Examples

Example of **incorrect** code:

```rust
struct Foo {
    x: i32,
    y: i32,
}
let x = 1;
let y = 2;

Foo { y, x };
```

Example of **correct** code:

```rust
Foo { x, y };
```

## Further Reading

* [Clippy - inconsistent_struct_constructor](https://clippy.rust-lang.org/stable/index.html#inconsistent_struct_constructor)

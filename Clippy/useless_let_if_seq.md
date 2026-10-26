Pattern: Mutable `let` assigned in following `if`

Issue: -

## Description

This is not idiomatic Rust.

## What it does

Checks for variable declarations immediately followed by a
conditional affectation.

## Examples

Example of **incorrect** code:

```rust
let foo;

if bar() {
    foo = 42;
} else {
    foo = 0;
}

let mut baz = None;

if bar() {
    baz = Some(42);
}
```

Example of **correct** code:

```rust
let foo = if bar() {
    42
} else {
    0
};

let baz = if bar() {
    Some(42)
} else {
    None
};
```

## Further Reading

* [Clippy - useless_let_if_seq](https://clippy.rust-lang.org/stable/index.html#useless_let_if_seq)

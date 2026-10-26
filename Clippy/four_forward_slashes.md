Pattern: Comment with four slashes (`////`)

Issue: -

## Description

This is (probably) a typo, and results in it not being a doc comment; just a regular
comment.

## What it does

Checks for outer doc comments written with 4 forward slashes (`////`).

## Examples

Example of **incorrect** code:

```rust
//// My amazing data structure
pub struct Foo {
    // ...
}
```

Example of **correct** code:

```rust
/// My amazing data structure
pub struct Foo {
    // ...
}
```

## Further Reading

* [Clippy - four_forward_slashes](https://clippy.rust-lang.org/stable/index.html#four_forward_slashes)

Pattern: Unused lifetime parameter

Issue: -

## Description

The additional lifetimes make the code look more
complicated, while there is nothing out of the ordinary going on. Removing
them leads to more readable code.

## What it does

Checks for lifetimes in generics that are never used
anywhere else.

## Examples

Example of **incorrect** code:

```rust
// unnecessary lifetimes
fn unused_lifetime<'a>(x: u8) {
    // ..
}
```

Example of **correct** code:

```rust
fn no_lifetime(x: u8) {
    // ...
}
```

## Further Reading

* [Clippy - extra_unused_lifetimes](https://clippy.rust-lang.org/stable/index.html#extra_unused_lifetimes)

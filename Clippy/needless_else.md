Pattern: Empty `else` branch

Issue: -

## Description

An empty else branch does nothing and can be removed.

## What it does

Checks for empty `else` branches.

## Examples

Example of **incorrect** code:

```rust
if check() {
    println!("Check successful!");
} else {
}
```

Example of **correct** code:

```rust
if check() {
    println!("Check successful!");
}
```

## Further Reading

* [Clippy - needless_else](https://clippy.rust-lang.org/stable/index.html#needless_else)
